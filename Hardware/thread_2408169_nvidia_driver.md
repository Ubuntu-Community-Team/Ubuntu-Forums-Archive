---
title: "nvidia driver"
date: 2018-12-14
forum: Hardware
---

### Post by lerantma on 2018-12-14
Hi all!




I have recently bought a computer and I am trying to install some nvidia drivers on it, but the following happens:


I am following the steps described here [https://www.pugetsystems.com/labs/hpc/How-To-Install-CUDA-10-together-with-9-2-on-Ubuntu-18-04-with-support-for-NVIDIA-20XX-Turing-GPUs-1236/](https://www.pugetsystems.com/labs/hpc/How-To-Install-CUDA-10-together-with-9-2-on-Ubuntu-18-04-with-support-for-NVIDIA-20XX-Turing-GPUs-1236/) (because I also would like to obtain CUDA 10). The steps I do is:
 - run "Software Updater"
 - restart
 - sudo apt-get install build-essential dkms
 - sudo apt-get install freeglut3 freeglut3-dev libxi-dev libxmu-dev
 - sudo dpkg -i cuda-repo-ubuntu1804_10.0.130-1_amd64.deb
 - sudo apt-key adv --fetch-keys [https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub](https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub)
 - sudo apt-get update
 - sudo apt-get install cuda
 - restart

After that, the computer is stuck in rebooting. The last thing it says is that gnome is started.
I have tried uninstalling gdm then reinstalling it, but that didn't help. I also tried uninstalling gdm and installing lightdm, but that time the system didn't boot either.


The linux version I use is Ubuntu 18.04.01 Desktop (64-bit) (I have tried both the LTS and non-LTS versions) from here: [https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)


My system's specs, which could maybe be a part of the problem:
 - ASUS ROG STRIX Z390-F motherboard
 - Intel i5-8600K
 - NVIDIA RTX 2080 (Gainward Phoenix)
 - monitor: HDMI, 2560x1080


Any help would be appreciated!


PS. Also, the following is the output in the terminal when installing cuda:
[https://paste.ubuntu.com/p/NvTZsPqXQY/](https://paste.ubuntu.com/p/NvTZsPqXQY/)

---

### Post by CatKiller on 2018-12-14
You haven't said what the actual problem is.

---

### Post by lerantma on 2018-12-14
Sorry, updated. Getting late here :S

---

### Post by CatKiller on 2018-12-14
So, to summarise:

You've installed the 410 proprietary driver, which seemed to go OK. On reboot you couldn't log in. You haven't said if you got a login window or not. Then you played around with different desktop managers. You're not sure if you're using gdm now, or lightdm, or neither. You couldn't make either of them work, in any case. Presumably you did this from a virtual terminal by using Ctrl-Alt-F2 or similar? You haven't said.

Is that accurate? It's details that we'll need.

You may find useful information in /var/log/Xorg.0.log about where it's got to in starting the X server, and where any problems may lie.

---

### Post by lerantma on 2018-12-17
It works!

It works thanks to you CatKiller - I read the Xorg.0.log file and it stated that more power cables should be connected to my GPU... I feel really ashamed now :S

---

### Post by CatKiller on 2018-12-17
Awesome. Glad it's fixed :smile:

---

