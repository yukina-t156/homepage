---
title: "QAOAリーディングメモ"
meta_title: ""
description: "this is meta description"
date: 2024-10-06
image: "/images/image-placeholder.png"
categories: ["QAOA", "研究"]
author: "Yukina Tatusta"
tags: ["メモ","論文"]
draft: false
---

簡潔に日本語訳・内容まとめながら読もうと思います。

Blekos, Kostas, et al. "A review on quantum approximate optimization algorithm and its variants." Physics Reports 1068 (2024): 1-66.

https://www.sciencedirect.com/science/article/pii/S0370157324001078

### 1. Introduction
### 2. Background

### 2.1. QUBO problems and applications
- QAOAはQUBO問題を解くためのもの
- QUBO問題はNP困難

### 2.2. MaxCut problem overview
最大カット問題の概要．
 
- 近似比率が0.9412を越える様な解を求める問題はNP困難らしい．
- 古典アルゴリズムの最良パフォーマンスは$\alpha\simeq 0.878$程度らしい

### 2.3. Classical algorithms for QUBO problem
{{< accordion "古典解法について" >}}
- Quadratic Programming
- Branch and Bound(B&B)
- Optimal methods
- Semidefinite Programming
- Interior-Point Method
- Heuristic methods
- Spectral clustering
- Goemans-Williamson algorithm
{{< /accordion >}}
一旦後回しにする

### 2.4. Variational quantum algorithms
- QAOAはVQAの一部

#### 2.4.1. Variational Quantum Eigensolver(VQE)
- ハイブリッドの解法
- $\theta$の最適化を行う
- 変分原理を利用

#### 2.4.2. Quantum Adiabatic Algorithm(QAA)

#### 2.4.3. Barren plateaus

### 2.5. The Quantum Approximate Optimization Algorithm(QAOA)

### 3. QAOA analysis

#### 3.1. Ansatz variants
回路の設計手法について．

{{< notice "note" >}}
Ansatz:
角度パラメータを持った回路 ([参考](https://blueqat.com/yuichiro_minato2/e1513e5c-2687-4f92-8ecb-b780e832941d#:~:text=%E5%AE%9F%E7%8F%BE%E3%81%97%E3%81%BE%E3%81%99%E3%80%82-,1%2D12.ansatz%EF%BC%88%E3%82%A2%E3%83%B3%E3%82%B6%E3%83%83%E3%83%84%EF%BC%89,-%E4%B8%8A%E8%A8%98%E3%81%AE))
量子回路の構造
{{< /notice >}}

$\hat{U}(\gamma,\beta)=e^{-i\beta_p\hat{H}_M}e^{-i\gamma_p\hat{H}_C}\cdots e^{-i\beta_1\hat{H}_M}e^{-i\gamma_1\hat{H}_C}$

- ansatzの選び方は問題による
  
当セクションではQAOAのansatzの設計やバリエーションについて紹介・議論する．

{{< accordion "table">}}
| Ansatz        |     概要      |  どうなった |
| ------------- | :-----------: | ----: |
|[ma-QAOA](#311-multi-angle-qaoa)|多角ansatz|深さを削減し近似率上昇|
|[QAOA+](#312-qaoa)|||
|[DC-QAOA](#313-digitized-counterdiabatic-qaoa)|||
|[ab-QAOA](#314-adaptive-bias-qaoa)|||
|[ADAPT-QAOA](#315-adapt-qaoa)|||
|[Recursive QAOA](#316-recursive-qaoa)|||
|[QAOAnsatz](#317-quantum-alternating-operator-ansatz)|||
|[GM-QAOA](#318-qarm-starting-qaoa)|||
|[Th-QAOA]()|||
|[Constraint Preserving Mixers]()|||
|[WS-QAOA]()|||
|[FALQON](#319-falqon)|||
|[FALQON+]()|||
|[FQAOA](#3110-fermionic-qaoa)|||
|[Quantum Dropout](#3111-quantum-dropout)|||
|[ST-QAOA](#3112-spanning-tree-qaoa)|||
|[Modified QAOA](#3114-modified-qaoa)|||

3113Ansatz architecture searchは？

{{< /accordion >}}

##### 3.1.1. Multi-angle QAOA
https://www.nature.com/articles/s41598-022-10555-8
- 変分パラメータ数を増やすことで近似率を上昇
> In ma-QAOA, new parameters are introduced into the circuit so that each element of the cost and mixer layers has its angle instead of one angle for the cost operator and one for the mixer operator


$$U_C(\gamma_l) = e^{-i\sum_{a=1}^{m}\gamma_{l,a}H_{C,a}} = \prod_{a=1}^{m}e^{-i\gamma_{l,a}H_{C,a}}$$

$$U_M(\beta_l) = e^{-i\sum_{v=1}^{n}\beta_{l,v}H_{M,v}} = \prod_{v=1}^{n}e^{-i\beta_{l,v}H_{M,v}}$$

  - $\gamma_{l, m}$: $l$はレイヤ，$m$はグラフの辺の数
  - $\beta_{l,m}$: $l$はレイヤ，$n$は頂点の数(=qubit数)
- コスト層，ミキサー層の各要素がそれぞれ角度のパラメータを持つ
  - 各要素とは？各量子ビットのこと？っぽい？
- 一般のQAOAはma-QAOAの一種：ビットやノードごとでのパラメータが一致したもの

##### 3.1.2. QAOA+
##### 3.1.3. Digitized counterdiabatic QAOA
##### 3.1.4. Adaptive bias QAOA
##### 3.1.5. ADAPT-QAOA
##### 3.1.6. Recursive QAOA
##### 3.1.7. Quantum alternating operator ansatz
##### 3.1.8. Qarm-starting QAOA
##### 3.1.9. FALQON
##### 3.1.10. Fermionic QAOA
##### 3.1.11. Quantum dropout
##### 3.1.12. Spanning tree QAOA
##### 3.1.13. Ansatz architecture search
##### 3.1.14. Modified QAOA

#### 3.2. Parameter optimization
パラメータの最適化手法について


