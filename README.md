# Risk-management-LPPL-PPO2-trader

## 강화학습(PPO2 알고리즘)과 위험성회피 전략(LPPL모델, Turblence index)을 적용시킨 트레이더

- 도구

  [![파이썬 Badge](https://img.shields.io/badge/python-3776AB?style=flat-square&logo=python&logoColor=white&link=mailto:wjtls01@naver.com)](mailto:wjtls01@naver.com)

  [![파이토치 Badge](https://img.shields.io/badge/pytorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white&link=mailto:wjtls01@naver.com)](mailto:wjtls01@naver.com)

  [![주피터 Badge](https://img.shields.io/badge/jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white&link=mailto:wjtls01@naver.com)](mailto:wjtls01@naver.com)

- 목표: 기존 PPO알고리즘 트레이더의 안정성과 수렴성 향상(PPO2) 및 리스크 회피

- 진행 이유: 논문을 읽던중 Turblence index를 사용하는 방법에 대해 알게 됐다. 또한 과거 LPPL 팀프로젝트를 진행한 경험이 있어<br/>
             강화학습 에이전트와 결합시키면 안정적인 트레이딩을 할 수 있을것이라 기대.


 
## 기능

## 요약

<br/>


## 본론

 - ## PPO2
   PPO는 new policy가 old policy 와 크게 다르지않도록 Clipping 하기 때문에 논문에서 안정성이 높고 빠르다는 결과를 보인다. <br/>
   또한 상승구간에서 타 에이전트에 비해 수익률이 잘나오는 편이다. 그러나 하락구간에서 A2C보다 낮은 샤프지수를 보인다.
 
 
 
## 결론

## 한계 및 개선
- 데이터의 노이즈로 인해 오버피팅 가능성 존재.<br/>
    - Denoise Auto Encoder(DAE) 방식으로 데이터의 노이즈 제거 가능<br/><br/>
- State의 정의 (차원의 저주 문제로 인해 1개의 feature만 사용)<br/>
    - 팩터들 사이에서 다중공선성 문제가 생길 수 있으므로 Feature Extraction 방법으로 차원의 저주와 높은 상관계수 문제 해결 예정<br/><br/>
- RDPG 알고리즘의 하이퍼파라미터 찾기가 타 에이전트에 비해 어려운편.<br/> 
    - Auto ML 방식으로 개선 예정<br/>
    - continuous action space에서 효과적인 다른 SOTA 에이전트 사용 (TD3,SLAC,SAC,D4PG 등등)<br/><br/>
- 시장은 t시점에서 알파를 찾아도 향후 새로운 알파가 생겨난다. <br/> 
    - 단일 에이전트 보다는 유동적으로 전략을 찾을수 있지만 현 앙상블 에이전트에서도 여전히 전략간 상관계수와 편향이 있다.  <br/> 
    - 더많은 에이전트를 앙상블하거나 MARL(Multi-Agent-Reinforcement-learning) 사용 예정   <br/>
    - 각 에이전트가 알고리즘 자체를 스스로 개선하도록 하여 여러 에이전트들의 전략간 상관계수와 편향을 낮출 예정

    
    






다중공선성

약한 정상성 시계열데이터가 약한정상성을 만족하려면
시계열데이터가 평균,분산이 시간에 의존하지않고 공분산은 시간이 아닌 시차(t의 텀)에만 의존해야함
이로인해 생기는 정상 시계열 모형 = MA, AR모형

약한의존성t=> inf로 갈때 상관관계가 0으로 수렴한다면 약한의존성 만족


약한정상성과 약한 의존성을 가진다면 대수의법칙 적용가능

대수의 법칙은 ‘경험적 확률과 수학적 확률과의 관계를 나타내는 정리(定理)’이다. 즉, 표본의 관측대상의 수가 많으면 통계적 추정의 정밀도가 향상된다는 것을 수학적으로 증명한 것이다. 이론적으로는 다음과 같다.

‘무한 모집단에서 무작위로 추출된 확률변수 X가 독립적으로 동일한 분포에 따르고 E(X)=μ, V(X)=σ2인 경우, 표본의 크기가 커짐에 따라 표본 평균 =∑xi/n은 확률적으로 모집단의 실제 평균값 μ에 수속(收束)한다
[네이버 지식백과] 대수의 법칙 [law of large numbers, 大數法則] (21세기 정치학대사전, 정치학대사전편찬위원회)

