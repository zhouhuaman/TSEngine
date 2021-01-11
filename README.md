# TSEngine,  an adaptive communication scheduler for efficient communication overlay in DML-WANs. 
In contrast to construct a static communication logic  before  the  training  job  starts,  TSEngine  adaptively optimizes  communication  logic  in  a  dynamically  scheduling  manner. 
As shown in Figure 1, In  TSEngine,  a global  coordinator  online  schedules  each  model  transmission  between  workers  and  the  parameter  server  based  on its  real-time  perception  of  the  network.
![image](https://github.com/zhouhuaman/TSEngine/blob/master/images/tsengine-overview.png)
Figure 1 Overview of TSEngine
MXNET is a popular, distributed machine learningframework.  The  PS-LITE library  is  an  implementation of  a  parameter  server  system  on  MXNET.  
In  our  work, we implement TSEngine as an independent communication scheduling layer of PS-LITE, which is located between theKV-APP layer and the VAN layer, as shown in Figure 2.
![image](https://github.com/zhouhuaman/TSEngine/blob/master/images/ts-arch-implementation.png)
Figure 2

## Deployment
1. Replace the source code of "3rdparty/ps-lite" and "src/kvstore" in MXNET(version 1.2.1) with modified codes in our repository. 
2. Deployment method is same as https://mxnet.apache.org/api/faq/distributed_training.html. 
3. Add two experiment variables for TSEngine on Scheduler, Server and Workerv in the startup script, as following:

   a. ENABLE_TS = 1;  // Enable the TSEngine function
   
   b. MAX_GREED_RATE=[0,1]; // The  maximum  probability  for  greedy  selection, which is a hyper-parameter given by the user  
   
Author: Huaman Zhou(hmzhou@std.uestc.edu.cn)， Weibo Cai(17719609705@163.com)
