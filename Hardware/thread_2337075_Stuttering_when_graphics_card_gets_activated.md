---
title: "Stuttering when graphics card gets activated"
date: 2016-09-14
forum: Hardware
---

### Post by oliems on 2016-09-14
Hi,

I have a problem. When my graphics card is not used my computer works fine (Image 1), but as soon as it is activated my computer starts to stutter (Image 2). Is there a way to fix this ? Maybe by using other drivers or by completely disabling the graphics card but I don't know how to do that as I'm very new to Ubuntu. ;)

I'm using the non-proprietary drivers and you can see more infos on my hardware on these screenshots : [http://imgur.com/a/VQOTa](http://imgur.com/a/VQOTa)

---

### Post by mörgæs on 2016-09-15
Hi, welcome to the fora.

How does it work in a live boot of some lighter environment, say X/Lubuntu?

---

### Post by oliems on 2016-09-15
I've tried a live boot of Lubuntu 16.04 and "radeon-pci-0200" doesn't seems to get activated. However I noticed that radeon-pci-0200 gets activated only when performing certain action like, in Ubuntu 16.04, opening the system settings. It also get's activated when opening the system settings on elementary OS 0.4 in live boot.

---

### Post by mörgæs on 2016-09-15
I assume stutter refers to the picture flickering, since you talk about the graphics card. Please correct me if I am wrong.

Radeon-pci-0200 looks like a sensor. Probably not relevant for the picture itself. 

Have you tried this? 
[https://help.ubuntu.com/community/RadeonDriver#Ubuntu_12.04.5_LTS_.28Linux_kernel_3.13.0.29.2C_Ubuntu_14.04_LTS_and_later](https://help.ubuntu.com/community/RadeonDriver#Ubuntu_12.04.5_LTS_.28Linux_kernel_3.13.0.29.2C_Ubuntu_14.04_LTS_and_later)

---

### Post by oliems on 2016-09-15
I experience micro-freeze with both video and sound when it is activated.

Yes, I tried but that does not seem to solve the problem.

---

### Post by mörgæs on 2016-09-17
If you have some extra space on the hard drive I suggest that you install Lubuntu 16.04.1 in a dual boot for comparison. 
Ubuntu might be too heavy for the hardware.

---

