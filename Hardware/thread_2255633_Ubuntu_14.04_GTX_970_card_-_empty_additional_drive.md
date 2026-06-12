---
title: "Ubuntu 14.04 GTX 970 card - empty additional drivers tab"
date: 2014-12-06
forum: Hardware
---

### Post by AgentZ86 on 2014-12-06
Hi

I had a GTX 650ti card working perfect on Ubuntu 14.04 64bit, 
I recently installed a new GTX 970 card and now when I login it freezes at splash screen once you login.
NO dash panel or icons just backround screen and non functional OS with a mouse I can move around on the backround screen but that is about it.

I tried to fix this and purged nvidia drivers and I can boot but there the additional drivers tab is empty

I did google and search the forums for varies solutions and tried them but it ends up with the same problem

Resorts back to freeze a login if I install the nvidia-current etc and so on.

Please advise
Thanks

---

### Post by AgentZ86 on 2014-12-06
I got it working, but not sure it was one or a combo of things I tried

This link had a post
[http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/]("http://ubuntuhandbook.org/index.php/2014/09/nvidia-343-22-install-in-ubuntu-1404/")

And at the bottom this part actually was the part that got things working with my GTX 970 card
> sudo add-apt-repository ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get install nvidia-343

However, I'm not entirely sure that this would have worked on it's own without first installing the CUDA toolkit from the nvidia site first
[https://developer.nvidia.com/cuda-downloads]("https://developer.nvidia.com/cuda-downloads")

I downloaded the *DEB version and then righclicked and opened with (SoftwareCenter)
The RUN version would not install with SoftwareCenter so I just used the .deb file

I do not know if this was needed in order for the posted commands to work properly for the 970 support.

But anyhow that is what I did and it is working now FYI

---

### Post by Yellow Pasque on 2014-12-06
I don't think the CUDA .deb was necessary. I generally recommend this PPA as it's less invasive than xorg-edgers. [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

---

### Post by Fozz on 2014-12-07
:)

---

### Post by Fozz on 2014-12-07
I'm sort of having the same problem I installed 343.22 and it ran the install but failed. I seem to have a basic driver running the card now (VESA: GM204 Board) but the res only offers 1024x768 and it seems like its not responding well


14.04 
Intel® Core&#8482; i7-4770K CPU @ 3.50GHz × 8
the MB is an ASUS Z87 Plus and the  Video card is an ASUS  gtx 970 if someone has a simple (easy step by step solution) I could use one. I'm NOT versed in cmd line but I follow instructions well...

---

### Post by Fozz on 2014-12-07
ok I got lucky and found a reference to Cuda 6.5 and installed that from a deb and now have 1920x1080 and seemly better speed / performance!!   :D

---

