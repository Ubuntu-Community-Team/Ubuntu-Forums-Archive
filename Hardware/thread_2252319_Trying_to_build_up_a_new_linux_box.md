---
title: "Trying to build up a new linux box"
date: 2014-11-11
forum: Hardware
---

### Post by zircon_34 on 2014-11-11
I checked, the last threads on building a linux box seem relatively old. There I go. 

I would like to upgrade my old pc and get some motivation to get back working on linux or maybe even switch as I really enjoy using it. For now I want to change the motherboard and buy a intel core i5 processor. Perhaps add an SSD drive not sure yet if its worth it. 

For the processor I was looking at intel i5-4590 or i5-4670 K with a motherboard ASRock Z97 Extreme 3, 4 or 6. Anyone tried this hardware with Ubuntu 14.04 or 14.10, any compatibility issues? 

Which SSD can you recommend? I though about a Samsung780 EVO 250 GB... 

Thanks for any input!;)

---

### Post by oldfred on 2014-11-11
I just built a new system with the intel i5-4590 and an Asus AR. The AR was not the correct board for my system as it had a display port video and that is not really working with Linux for now. And only other connection was HDMI but my monitor is DVI. Adapters made it work but I would have been better off with different motherboard.
I think the board is more for gamers which I am not. And even though the CPU is for overclocking I will not use that. 

The AR also required many UEFI settings to get it to boot in UEFI mode. It has a Window or Other setting which I assume is really secure boot? Then I could only find UEFI settings under CSM. I would think it should be UEFI or CSM but only in the CSM sub-menu was UEFI. And the UEFI or CSM with UEFI first would not even work. I could only use UEFI only to boot flash drive.

I got a 128GB SSD Samsung Pro model and 1TB drive, but am wondering what to do with all that space. I do not have videos and now photos of grandson take most of the space.
I had an old 64GB SSD and had two 28GB / (root) partitions, so on new system I installed with 25GB root. Now what to do with remaining 100GB on SSD? At least one more install and maybe some often used data?
All my data is on 1TB drive in data partitions. 
System is really fast booting & loading larger apps, but somehow it does not make me type any faster?

---

### Post by zircon_34 on 2014-11-13
Is the internal graphic card of your cpu satisfying or did you buy an extra card? I have no experience with uefi, hope the ubuntu install will go smoothly...

---

### Post by oldfred on 2014-11-13
I did not think UEFI install with my system was smooth at all. But once I got all UEFI settings correct then I could boot flash drive in UEFI mode & it did work well. 
I always partition in advanced and use Something Else to install.

I have not yet tested internal Intel graphics. I had to buy a new cable and now system is back against wall. And right now it is not particularly easy to unplug & test so I have not done that yet.
I had a nVidia 620Gt card which had DVI connections so I could use existing cables. And that has worked well.

fred@trusy-ar:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 620] (rev a1)

With my old dual core Intel system and nVidia 9600GT, I always had to use nomodeset until I installed nVidia drivers. I have not installed nVidia driver yet, either. But I get a minor bit of screen tearing only when posting replies here? Have run some videos without issue.
Part of reason I did not install nVidia drivers, yet was I had planned on testing the Intel video. But now not sure when I may get to it.

---

