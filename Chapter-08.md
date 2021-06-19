# Chapter8-Multiuser Radio Communications

[TOC]

## 8.1 Introduction

### Multiuser Radio Communication

> Simultaneous use of a communication channel by a number of users

### Ideal communication channel

> 带限信道+高斯白噪声

## 8.2 Multiple-Access Techniques

> Multiple access is a technique whereby many subscribers or local stations can share the use of a communication channel at the same time or nearly so.
>
> State in another way, a multiple-access technique permits the communication resources of the channel to be shared by a large number of users communicating with each other.

<img src="https://figure-leaf.oss-cn-beijing.aliyuncs.com/img/image-20210615185254291.png" alt="image-20210615185254291" style="zoom:67%;" />

**多址接入的 4 种基本类型**

> Allocating the communication resources of the channel through the use of disjointedness (or orthogonality in a loose sense) in time, frequency, or space.

``FDMA``

> Disjoint sub-band of frequency are allocated to the different users.
>
> Guard bands are used to act as buffer.

``TDMA``

> Guard bands are used to act as buffer.
>
> Buffer zones in the form of guard times are inserted between the assigned time slots for reducing interference.

``CDMA``

> An important advantage of CDMA over both FDMA and TDMA is that it can provide for secure communications.

``SPMA``

> Resource allocation is achieved by exploiting the spatial separation of the individual users 
>
> (E. g. Multibeam antennas –different directions).

## 8.3 Satellite Communications

| Summary                                                      |
| ------------------------------------------------------------ |
| Uplink & downlink 6/4GHz or 14/12Hz                          |
| Line-of-sight radio propagation for the operation of its uplink and downlink |
| Additive white Gaussian noise channel model                  |
| Offers global coverage                                       |
| TDMA used widely in digital satellite communication          |

> 卫星通信的频带：上行6GHz(C-band)；下行4GHz
>
> We develop 14/12GHz frequency band.

<img src="https://figure-leaf.oss-cn-beijing.aliyuncs.com/img/image-20210615185734541.png" alt="image-20210615185734541" style="zoom: 50%;" />

<img src="https://figure-leaf.oss-cn-beijing.aliyuncs.com/img/image-20210615193309697.png" alt="image-20210615193309697" style="zoom:50%;" />

**上行链路信号(接收天线)$\rightarrow$带通滤波器$\rightarrow$低噪声放大器$\rightarrow$下变频$\rightarrow$传输波导放大器$\rightarrow$下行链路信号(发射天线)**

> Other channel configurations do the frequency conversion from the uplink to the downlink frequency in two stages: down-conversion to an intermediate frequency, followed by amplification, and the up-conversion to the desired transmit frequency.

**Satellite Channel**

> 1. 长距离$\rightarrow$传播时延高，需要自适应消除回响
> 2. 上下行链路和AWGN模型相似，可使用AWGN信道的分析方法

**Satellite Transponder**

> 不同于传统，许多地面站可以几乎在同一时间从地球上不同位置访问卫星

**Observations**

> 1. 转发器的非线性$\rightarrow$干扰$\rightarrow$行波管放大器故意低于容限$\rightarrow$FDMA系统的功率效率降低
> 2. 在TDMA系统中，用户一次一个地访问卫星转发器$\rightarrow$卫星转发器可以接近全功率运行$\rightarrow$TDMA比FDMA更有效地使用转发器$\rightarrow$TDMA技术在数字卫星通信中得到了广泛的应用

## 8.4 Radio Link Analysis

> 卫星通信系统设计中的一个重要问题——链路(功率)预算分析——在运行一条通信链路时产生的所有增益和损失的总和

**Link Margin (链路余量)**

<img src="https://figure-leaf.oss-cn-beijing.aliyuncs.com/img/image-20210615200752542.png" alt="image-20210615200752542" style="zoom: 67%;" />
$$
(\frac{E_b}{N_0})_{rec}=M(\frac{E_b}{N_0})_{req}
\\
M(dB)=(\frac{E_b}{N_0})_{rec}(dB)-(\frac{E_b}{N_0})_{req}
$$
链路余量M越大，通信链路的可靠性越好，以信噪比为代价。

### 8.4.1 Free-Space Propagation Model (自由空间模型)

**计算接收信号功率**

> This calculation accounts for all gains and losses incurred in the transmission and reception of the carrier.

**Antennas**

> 发射天线和接受天线
>
> 发射天线：将电调制信号转换为电磁信号，在预定方向辐射。
>
> 接收天线：将电磁场转换为电信号，从中提取调制信号。抑制来自不需要方向的辐射。

**"Reference" antenna**

> 发射天线和接收天线的性能可以与参考天线进行比较。
>
> 在实际应用中，假设参考天线为各向同性源(向各个方向均匀辐射)。

**Power density**

> 考虑一个辐射总功率(瓦特)的各向同性源。因此，功率密度$\rho(d)$为：
> $$
> \rho(d)=\frac{P_t}{4\pi d^2}
> $$
> 功率密度与距离的平方成反比

**Radiation intensity (辐射强度)**

> $$
> \Phi=d^2\rho(d)
> $$
>
> 辐射强度$\Phi$是每单位立体角的功率

<img src="https://figure-leaf.oss-cn-beijing.aliyuncs.com/img/image-20210615202601691.png" alt="image-20210615202601691" style="zoom: 50%;" />

**Directive Gain, Directivity, and  Power Gain**

> 定向增益或指向性，天线将辐射功率集中到一个给定方向(发射天线)或从该方向吸收入射功率的能力
>
> **定向增益**定义为：
> $$
> g(\theta,\phi)=\frac{\Phi(\theta,\phi)}{P_{av}}=\frac{\Phi(\theta,\phi)}{P/(4\pi)}
> $$
> 天线的方向性——方向性增益的最大值$g(\theta,\phi)$，它是一个常数，在一个特定的方向上被最大化。
>
> 天线的**功率增益G**——天线的最大辐射强度与无损各向同性源的辐射强度之比。
> $$
> G=\eta_{radiation}D
> $$
> 其中，$\eta$ 为天线的辐射效率因子。

<img src="https://figure-leaf.oss-cn-beijing.aliyuncs.com/img/image-20210615204556750.png" alt="image-20210615204556750" style="zoom:50%;" />

**Two parameters**

> **EIRP (Effective radiated power referenced to an isotropic source)**
> $$
> EIRP=P_tG_t
> $$
> **Antenna beamwidth (天线波束宽度)**
>
> 天线的功率增益越高，天线的波束宽度越窄。

**Effective Aperture (有效孔径，特别是接收天线)**

> The effective aperture, denoted by A, is defined as
> $$
> A=\frac{\lambda ^2}{4\pi}G
> $$

**Friis Free-Space Equation**

> 考虑一个发射天线
> $$
> EIRP=P_tG_t
> $$
> 平方反比定律
> $$
> \rho(d)=\frac{P_t}{4\pi d^2}
> $$
> 那么功率密度可以表示为
> $$
> EIRP/(4\pi d^2)
> $$
> 接收功率 $P_r$ 可以表示为
> $$
> P_r=(\frac{EIRP}{4\pi d^2})A_r
>    =P_tG_tG_r(\frac{\lambda}{4\pi d})^2
> $$

**The path loss (PL)**

> 用 dB 表示整个通信链路上的信号“衰减”，定义为
> $$
> PL=10\log_{10}(\frac{P_t}{P_r})=-10\log_{10}(G_tG_r)-10\log_{10}(\frac{\lambda}{4\pi d})^2
> $$

### 8.4.2 Noise Figure

> 器件的噪声系数与其噪声温度 $T_e$ 有关
> $$
> F=1+\frac{T_e}{T}
> \\
> T_e=T(F-1)
> \\
> N_0=kT_e
> $$

### 8.4.3 Downlink Budget Analysis of a Digital Satellite Communication System

> $$
> (\frac{C}{N_0})_{downlink}=(EIRP)_{satelliate}(\frac{G_r}{T_e})_{earth\ terminal}(\frac{\lambda}{4\pi d})^2\frac{1}{k}
> \\
> (\frac{C}{N_0})_{downlink}=(\frac{E_b}{N_0})_{req}+10\log_{10}M+10\log_{10}R
> $$

## 8.5 Wireless Communications



## 8.6 Statistical Characterization of Multipath Channels

<img src="https://figure-leaf.oss-cn-beijing.aliyuncs.com/img/image-20210616141548847.png" alt="小尺度衰落" style="zoom:50%;" />

| **Four important parameters**     |
| --------------------------------- |
| **1. Delay Spread $\sigma_\tau$** |
| **2. Doppler Spread $\sigma_v$**  |
| **3. Coherent Bandwidth $B_c$**   |
| **4. Coherent Time $\tau_c$**     |

> 相干带宽与时延扩展倒数关系，相干时间与多普勒拓展倒数关系
> $$
> B_c=\frac{1}{\sigma_{\tau}}\hspace{2cm}
> \tau_c=\frac{1}{\sigma_{v}}
> $$

<img src="https://figure-leaf.oss-cn-beijing.aliyuncs.com/img/image-20210616141630099.png" alt="image-20210616141630099" style="zoom:50%;" />

## 8.7 Binary Signaling over a Rayleigh Fading Channel

> **For AWGN channel**
> $$
> \widetilde{x}(t)=\widetilde{s}(t)+\widetilde{w}(t)
> \\
> P_e=\frac{1}{2}erfc(\sqrt{\gamma})
> $$
> **For Rayleigh fading channel**
> $$
> \widetilde{x}(t)=\alpha\exp(-j\phi)\widetilde{s}(t)+\widetilde{w}(t)
> \\
> P_e=\frac{1}{2}(1-\sqrt{\frac{\gamma_0}{1+\gamma_0}})\rightarrow\frac{1}{4\gamma_0}
> $$

**Problem: 大幅提高平均信噪比以对抗衰落**

**Solution: 分集技术**

:one:**Frequency diversity**

> 信息信号使用多个载波传输，这些载波彼此之间间隔足够远，以提供信号的独立衰落版本。选择等于或大于信道相干带宽的频率间隔来实现

:two:**Time diversity**

> 同一信息信号在不同时隙中传输，连续时隙之间的间隔等于或大于信道的相干时间。这可以通过使用错误控制编码的重复代码来实现。

:three:**Space diversity**

> 采用多个发射或接收天线(或同时使用)，选择相邻天线之间的间距，以保证衰落事件的独立性;这可以通过将相邻天线间隔至少为无线电波长的7倍来实现。

**Liner diversity combining structure**

> :heavy_check_mark:Selection Combining
>
> :heavy_check_mark:Equal Gain Combining
>
> :heavy_check_mark:Maximal Ratio Combining

<img src="https://figure-leaf.oss-cn-beijing.aliyuncs.com/img/image-20210616150814961.png" alt="image-20210616150814961" style="zoom:50%;" />

## 8.8 TDMA and CDMA Wireless Communication Systems

### 8.8.1 How to distinguish uplink and downlink?

> :heavy_check_mark: FDD: Frequency division duplexing
>
> :heavy_check_mark: TDD: Time division duplexing

### 8.8.2 How to distinguish different users?

> :heavy_check_mark: GSM: uses TDMA
>
> :heavy_check_mark: IS-95: uses CDMA

## 8.9 Source Coding of Speech for Wireless Communications

## 8.10 Adaptive Antenna Arrays for Wireless Communications

> 无线通信的目标是允许尽可能多的用户在不考虑位置和移动性的情况下进行可靠的通信。
>
> From the discussion presented in Sections 8.5 and 8.6, we find this goal is seriously impeded by three major channel impairments: multipath, delay spread and co-channel interference.

**Multipath **

**Delay spread **

**Co-channel interference (CCI) **

## 8.11 Summary and Discussion

**Two multiuser communications**

| **satellite communication (global coverage)** |
| --------------------------------------------- |
| **wireless communication (mobility)**         |

**satellite communication**

> :heavy_check_mark: uplink: earth terminal$\rightarrow$satellite
>
> :heavy_check_mark: downlink: satellite$\rightarrow$earth terminal
>
> :heavy_check_mark: line-of-sight path
>
> :heavy_check_mark: additive white Gaussian noise channel

**wireless communication**

> :heavy_check_mark: co-channel interference
>
> :heavy_check_mark: multipath$\rightarrow$fading
>
> :heavy_check_mark: delay spread
>
> :heavy_check_mark: specialize techniques used, such as:
>
> :heavy_check_mark: Diversity, adaptive array antennas, RAKE receiver
