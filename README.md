# Update1
[retinaface_mnet025_v1](http://insightface.ai/files/models/retinaface_mnet025_v1.zip)
[retinaface_mnet025_v2](http://insightface.ai/files/models/retinaface_mnet025_v2.zip)
In mxnet symbol, BN has fix_gamma, if fix_gamma is true, then set gamma to 1 and its gradient to 0, you can find this in mxnet API.
for example, in retinaface_mnet025_v1, the output is different from 'conv_3_dw_batchnorm', because fix_gamma in 'conv_3_dw_batchnorm' is true，but its value is 0.000007107922556315316(you can see weight by Netron). So forward onnx model its('conv_3_dw_batchnorm') gamma is 0.000007107922556315316, but forward mxnet model, actually its'conv_3_dw_batchnorm' gamma is 1.

# Update  
Retinaface fixed softmax bug.  
Upsample is implemented using Resize.  
Upsample is implemented using ConvTranspose.  

# arcface_retinaface_mxnet2onnx
arcface and retinaface model convert mxnet to onnx
# environment
MxNet 1.5.0  
onnx 1.7.0 (protobuf 3.0.0)  
onnxruntime 1.3.0  
Python 3.6.9  
cv2 3.3.1  
# tested models
arcface:from [ZQCNN](https://github.com/zuoqing1988/ZQCNN) [mobilefacenet-res2-6-10-2-dim512](https://pan.baidu.com/s/1_0O3kJ5dMmD-HdRwNR0Hpw#list/path=%2F)  
retinaface:[mnet.25](https://link.zhihu.com/?target=https%3A//github.com/deepinsight/insightface/issues/669)  

# arcface  
[Insightface中ArcFace MxNet2ONNX踩坑](https://zhuanlan.zhihu.com/p/165294876)  

# retinaface  
[Insightface中Retinaface MxNet2ONNX踩坑](https://zhuanlan.zhihu.com/p/166267806)  

# Results
![arcface onnx_mxnet_output](https://github.com/zheshipinyinMc/arcface_retinaface_mxnet2onnx/tree/master/Arcface/onnx_mxnet_output.jpg)  
![retinaface onnx_mxnet_output](https://github.com/zheshipinyinMc/arcface_retinaface_mxnet2onnx/tree/master/Retinaface/mxnet_onnx_result.jpg)  

# reference
[insightface](https://github.com/deepinsight/insightface)
