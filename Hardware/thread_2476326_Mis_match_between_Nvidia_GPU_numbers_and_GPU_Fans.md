---
title: "Mis match between Nvidia GPU numbers and GPU Fans"
date: 2022-06-23
forum: Hardware
---

### Post by jjziets on 2022-06-23
Im trying to get the gpu temps down fo my servers. I have noticed that when I set the fan speed the corresponding fans does not follow the GPU index numbers. 


 
This is a headless server running Ubuntu 20.04.4 LTS 
Nvidia drivers NVIDIA-SMI 515.48.07 


here is a snippet of the code 


```
SET='/usr/bin/nvidia-settings'


       xinit ${SET}     -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUTargetFanSpeed=${Fspeed[2]} \
            -a [gpu:1]/GPUFanControlState=1 -a [fan:1]/GPUTargetFanSpeed=${Fspeed[3]} \
            -a [gpu:2]/GPUFanControlState=1 -a [fan:2]/GPUTargetFanSpeed=${Fspeed[0]} \
            -a [gpu:3]/GPUFanControlState=1 -a [fan:3]/GPUTargetFanSpeed=${Fspeed[1]} --  :0

```

the rest of the code can be found here. [https://github.com/jjziets/nvidia-fan-control-linux/blob/master/fan-control4.sh](https://github.com/jjziets/nvidia-fan-control-linux/blob/master/fan-control4.sh) 

it looks like the fans are shifted by 2 but on the 8 gpus sytems its just plain random [https://github.com/jjziets/nvidia-fan-control-linux/blob/master/fan-control8.sh](https://github.com/jjziets/nvidia-fan-control-linux/blob/master/fan-control8.sh)


to set fan on GPU0 I need to change fan 2 and for GPU 1 set fan 3 if I set GPU N with Fan N its is mismatched.


I have tested this on several systems and the logic remains.

any suggestions on why this is?

---

### Post by jjziets on 2022-06-30
Am I doing something wrong? Am I the only one that is running more than one gpu?

---

### Post by #&amp;thj^% on 2022-06-30
> **jjziets said:**
> Am I doing something wrong?

Not as far as the forums go.
> **jjziets said:**
> Am I the only one that is running more than one gpu?
No! that's just silly.
I used a mix of this link: [http://bailiwick.io/2019/09/21/controlling-nvidia-gpu-fans-on-a-headless-ubuntu-system/](http://bailiwick.io/2019/09/21/controlling-nvidia-gpu-fans-on-a-headless-ubuntu-system/)
```
nvidia-smi --query-gpu=timestamp,gpu_bus_id,utilization.gpu,utilization.memory,temperature.gpu,fan.speed,power.draw --format=csv

timestamp, pci.bus_id, utilization.gpu [%], utilization.memory [%], temperature.gpu, fan.speed [%], power.draw [W]
2022/06/30 15:11:58.136, 00000000:01:00.0, 5 %, 7 %, 39, [N/A], 3.29 W

```

---

