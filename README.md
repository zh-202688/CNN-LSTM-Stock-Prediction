# CNN-LSTM Stock Prediction


## 📖 项目介绍 (Introduction)

本项目是一个基于深度学习的金融时间序列预测系统。旨在通过构建 **CNN-LSTM 混合神经网络模型**，对 **上证综合指数 (000001.SH)** 的收盘价趋势进行预测。

项目核心在于利用一维卷积神经网络 (1D-CNN) 提取 K 线图中的局部高频形态特征，并结合长短期记忆网络 (LSTM) 捕捉长期时序依赖。实验结果表明，该混合架构在 RMSE、MAE、MAPE 等指标上均显著优于单一 LSTM 基准模型，且性能提升通过了配对样本 T 检验 (P-value < 0.05)。

### ✨ 核心特性
* **多源特征融合**：整合 OHLCV 基础行情及 MA5、MA20、日收益率等 8 维特征。
* **混合模型架构**：CNN (特征提取) + LSTM (时序建模) + Dropout (防过拟合)。
* **真实数据源**：通过 BaoStock 接口实时获取 A 股历史数据，无需手动下载 CSV。
* **严谨验证**：包含完整的训练可视化、反归一化评估及统计学显著性检验。

## 📊 实验结果 (Results)

基于 2015-2023 年的上证指数数据测试，改进模型表现如下：

============================================================
Metric     | Baseline (LSTM)      | Improved (CNN-LSTM) 
------------------------------------------------------------
RMSE       | 31.4880                | 28.4796
MAE        | 24.5454                | 22.2822
MAPE       | 0.7770%               | 0.7052%
R2         | 0.9260                | 0.9394
============================================================

统计检验 P-value: 3.23380e-03
结论: 改进模型具有【统计学显著性】的性能提升。

### 📉 效果可视化

| 训练损失收敛 (Training Loss) | 预测结果对比 (Prediction Comparison) |
| :---: | :---: |
| ![Loss Curve](<img width="1084" height="832" alt="image" src="https://github.com/user-attachments/assets/b93fdd71-20bd-4c04-aa71-cfb964c62752" />) 

| ![Prediction](<img width="1066" height="848" alt="image" src="https://github.com/user-attachments/assets/7fe2029c-91ef-4095-849d-611e3ae317ba" />
) |

## 🛠️ 环境依赖 (Requirements)

本项目基于 Python 3.10 开发，主要依赖库如下：

* `tensorflow >= 2.6.0`
* `baostock` (数据获取)
* `pandas` & `numpy`
* `matplotlib` (绘图)
* `scikit-learn` (归一化)
* `scipy` (统计检验)

你可以通过以下命令一键安装：

```bash
pip install tensorflow baostock pandas numpy matplotlib scikit-learn scipy
