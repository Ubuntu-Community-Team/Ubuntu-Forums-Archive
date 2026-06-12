---
title: "Nvidia drivers for headless CUDA blender cycles"
date: 2015-12-08
forum: Hardware
---

### Post by fen-openprivacy on 2015-12-08
I have a GTX 970 GPU that I want to use on a headless blender cycles/render machine running Ubuntu 14.04 server. My question is: how can you install the Nvidia CUDA drivers without pulling in the entire GUI environment?

I started with this from [https://developer.nvidia.com/cuda-downloads-geforce-gtx9xx](https://developer.nvidia.com/cuda-downloads-geforce-gtx9xx) :
```
wget http://developer.download.nvidia.com/compute/cuda/6_5/rel/installers/cuda-repo-ubuntu1404-6-5-prod_6.5-19_amd64.deb
sudo dpkg -i cuda-repo-ubuntu1404-6-5-prod_6.5-19_amd64.deb
```

But then [FONT=courier new]`sudo apt-get -s install cuda`[/FONT] reports that it will install 586 new packages, including xserver-xorg and unity-control-center, neither of which I want or need on a headless machine. (Well, the X libraries may be needed, but there's absolutely no need for unity...) Is there a leaner way to go about this?

---

### Post by fen-openprivacy on 2015-12-10
SOLVED: Following instructions at [http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html](http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html) I downloaded the CUDA toolkit from [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads) and used the runfile installer. PASSed deviceQuery and bandwidthTest operations with flying colors!

---

