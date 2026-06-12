---
title: "Problem with monitor or video card Ati Mobility X2300"
date: 2010-07-06
forum: Hardware
---

### Post by Fred2040 on 2010-07-06
Hello, I have  some problems with my monitor or video card. Following  happens: I see a lot of lines when I use Ubuntu Desktop "10.4." (It's like some TV, but with the distorted signal)...  with older  versions of Ubuntu didn't have this problem. I  really don't know which device is failing, the monitor or the graphics  card driver? But I'm sure this isn't the best  configuration. I currently working in a notebook,  Centino Duo, ATI Mobility X2300. The screen is  generic. (Obviously the laptop screen), etc. Also, I try another distro and works well. 
If anyone can help me thank you very much. 
:)

Best regards. 
Fred

---

### Post by Yellow Pasque on 2010-07-06
Try updating the driver. Boot to recovery mode and:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Fred2040 on 2010-07-06
> **Temüjin said:**
> Try updating the driver. Boot to recovery mode and:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

FYI, 
1st Step
$ sudo apt-add-repository ppa:xorg-edgers/ppa
Executing: ....
gpg: key 8844C542: "Launchpad PPA for xorg crack pushers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

2nd Step 
Reading package lists... Done

3rd Step
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
  libdrm-nouveau1: Breaks: xserver-xorg-video-nouveau (< 1:0.0.16) but 1:0.0.15+git20100219+9b4118d-0ubuntu5 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

It seems doesn't work! 
TY

---

### Post by Yellow Pasque on 2010-07-06
nouveau is the open nvidia driver. You don't need it:
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo apt-get dist-upgrade
```

---

### Post by Fred2040 on 2010-07-06
> **Temüjin said:**
> nouveau is the open nvidia driver. You don't need it:
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
sudo apt-get dist-upgrade
```


I did it, in root mode, but it doesn't work, my instalation is still with weird lines. I think is some incompatibility with my graphic card, because this lines are come from live cd... 
I also tried to reload old official Ati drivers, but we know it doesn't works fine too.. 
Maybe I have to wait, while somebody upgrade a fixed drivers..

But, I really appreciate your help... 


Best regards..

Fred

---

### Post by iknatius on 2010-08-16
> **Fred2040 said:**
> I did it, in root mode, but it doesn't work, my instalation is still with weird lines. I think is some incompatibility with my graphic card, because this lines are come from live cd... 
I also tried to reload old official Ati drivers, but we know it doesn't works fine too.. 
Maybe I have to wait, while somebody upgrade a fixed drivers..


Hi Fred,

Any progress trying to make your x2300 run?. I am exactly with the same  problem (ASUS A8J with Mobility Radeon x2300 trying to make 10.04 run) and no progress at this  moment.
I have just made the edgers upgrade but... still nothig :(

THX in advance,

iknatius

---

### Post by bestgun on 2011-02-10
> **Temüjin said:**
> Try updating the driver. Boot to recovery mode and:
```
sudo apt-add-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

I did it and it works for me!
My problem was the same as Fred2040 but I have a MacBook Pro first generation with an ATI Radeon Mobility X1600.

Tks people!

---

