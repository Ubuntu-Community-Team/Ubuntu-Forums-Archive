---
title: "graphic card not recognized on UBUNTU 18.04.3 LTS"
date: 2019-08-23
forum: Hardware
---

### Post by gowkster on 2019-08-23
Hello all.

For years I have a computer with Ubuntu with an old graphics card that today I decided to update for a 1080TI but ubuntu recognizes it as a GTX 760, which is the one I had previously installed. 

when i do..: $ nvidia-smi , it show :

Fri Aug 23 17:50:56 2019       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 418.87.00    Driver Version: 418.87.00    CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 760     On   | 00000000:01:00.0 N/A |                  N/A |
| 26%   47C    P0    N/A /  N/A |    244MiB /  4033MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+

Can somebody help me?

---

### Post by TheFu on 2019-08-23
Did you buy it from a reputable, brick and mortar, store?
There are a bunch of fakes being sold online and have been since crypto-currency mining started.
There are youtube channels just about picking out fake video cards.
[https://www.reddit.com/r/pcgaming/comments/7l3nir/ebay_is_being_flooded_with_fake_gpus/](https://www.reddit.com/r/pcgaming/comments/7l3nir/ebay_is_being_flooded_with_fake_gpus/)

---

### Post by gowkster on 2019-08-23
It is a used Gigabyte 1080 IT that I bought from a friend, it was a few years it is a gaming computer ...
the graphic card referred by the Nvidia-SMI is the one I had until yesterday

---

### Post by deadflowr on 2019-08-23
Did you just swap out the old card and not reset the driver and config settings?

---

### Post by overdrank on 2019-08-23
Hi and welcome. Just my thoughts, did you uninstall the Nvidia driver before installing the different graphics card?
Ooops deadflowr beat me to it :)

---

### Post by gowkster on 2019-08-23
> **deadflowr said:**
> Did you just swap out the old card and not reset the driver and config settings?

I changed the card and put the following commands:
```

[[FONT=Menlo]sudo apt-get purge nvidia*
[/FONT]wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin
sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
sudo add-apt-repository "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/ /"
sudo apt-get update
sudo apt-get -y install cuda
[FONT=Menlo]
[/FONT]
```

but I think something I have done wrong, because in software and updates it shows me in additional controls all these options:


Nvidia driver metapackage nvidia-driver-430
Nvidia driver metapackage nvidia-driver-418
Nvidia binary driver -version 340.107
Nvidia driver metapackage nvidia-driver-410
Nvidia driver metapackage nvidia-driver-390
X.ORG Xserver - Nouveau display driver

---

### Post by gowkster on 2019-08-23
> **overdrank said:**
> Hi and welcome. Just my thoughts, did you uninstall the Nvidia driver before installing the different graphics card?
Ooops deadflowr beat me to it :)
I think so, but I'm not sure I did it right

---

### Post by TheFu on 2019-08-23
If you are using 18.04 or 16.04, then the correct nvidia drivers should be loaded using the "Get Additional Drivers" just fine. No need for other PPAs since mid-July.

[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its) has more details.
Best not to get drivers directly from vendors if the standard Ubuntu driver offers anything.

---

### Post by gowkster on 2019-08-23
> **TheFu said:**
> If you are using 18.04 or 16.04, then the correct nvidia drivers should be loaded using the "Get Additional Drivers" just fine. No need for other PPAs since mid-July.

[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its) has more details.
Best not to get drivers directly from vendors if the standard Ubuntu driver offers anything.
Do you know how to delete old versions?

```

~$ ubuntu-drivers devices 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001187sv00001458sd00003614bc03sc00i00
vendor   : NVIDIA Corporation
model    : GK104 [GeForce GTX 760]
driver   : nvidia-340 - distro non-free
driver   : nvidia-driver-430 - third-party free recommended
driver   : nvidia-driver-418 - third-party free
driver   : nvidia-driver-410 - third-party free
driver   : nvidia-driver-415 - third-party free
driver   : nvidia-driver-390 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin



```

but "sudo apt-get purge nvidia*" has no effect

---

### Post by TheFu on 2019-08-23
Any information in /sys and /proc are virtual file systems created by the kernel based on what it discovers at boot.

```
sudo lshw -C video 
```
is how I'd see what is really in the system.  Bet it shows *GeForce GTX 760*. Your friend might have been taken with a fake.

On my 1030 system, the driver updated automatically. It had an unsupported Quattro GPU before. I wanted the cheapest GPU that supported HEVC/AC1 encoding in hardware, expecting transcoding software to catch up eventually.

---

### Post by gowkster on 2019-08-24
First of all, apologize.

I was talking to my friend and he told me that the card he gave me was indeed a GeForce GTX 760, not a 1080TI as I thought.
so I want to apologize to the forum for my useless question.

Now we only have to operate the CUDA drivers properly and it is already

---

### Post by TheFu on 2019-08-24
> **gowkster said:**
> First of all, apologize.

I was talking to my friend and he told me that the card he gave me was indeed a GeForce GTX 760, not a 1080TI as I thought.
so I want to apologize to the forum for my useless question.

Now we only have to operate the CUDA drivers properly and it is already

No worries. We all have done something similar. Glad you came back and reported it. We've all been there.
Please use the "Thread Tools" button near the top of the page to mark the thread SOLVED. That helps both parts of the community here.

---

