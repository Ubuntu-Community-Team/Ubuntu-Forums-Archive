---
title: "Problem with graphics and Secure Boot and ASUS TUF505DU-EB74"
date: 2019-07-25
forum: Hardware
---

### Post by soulsurfer2 on 2019-07-25
So, Bought a new laptop. An ASUS TUF TUF505DU-EB74.  I installed UBUNTU 18.04.2 and I [FONT=arial]cant get it out of 800x600 mode.  I'm pretty sure its an issue with the NVIDIA driver and Secured boot.  Any ideas?[/FONT]

---

### Post by djwitkac on 2019-08-10
Hi 

I had similar issues on ausus Tuf 505 DU however on different linux distros. On Linux Mint I needed to upgrade Kernel to 5.2 to be able to use native fullHD resolution.
On Ubuntu 19.04 which I downloaded and installed last week it was all good and resolution is native fullHD since scratch.
However to be able to force this laptop to use nvidia instead of AMD Ryzen 7 graphics is different story. Trying to make it work and use fully with nvidia but without success in that case so far ;(
Waiting for Centos 8 to give it a try once more. It looks like it's related to Xorg bug for AMD processors so far ;( at least it looks like the issue blocking nvidia ;(

---

### Post by djwitkac on 2019-08-12
update: <br><br>If You are planning using Your laptop for things related to GPU calculations etc. and system natively doesn't pick up Nvidia as a default card or showing infos that the card is not used it might be also wrong info from the system itself.<br>When I'm running 3D applications and checking by them which graphics card is really used I have a infos and stats that GPU is fully utilized ! It take me a while to check it and test it out. It's working ;)<br>Ubuntu 19.04 Laptop TUF FX 505 DU and latest bios 306 . Not going to switch to other Linux for now. Yuppy ! ;)

p.s will test it also on games to see if they enforce to use GPU too.

---

### Post by msrr18 on 2019-08-15
Hello, can you please tell me how did you install Ubuntu on your lappy? I have almost the same lappy.

---

### Post by anand31 on 2019-08-18
i bough Asus ROG Strix G531GT.. no display issues but ... these laptops comes with aura lighting ... and i am not able to disable them which drain the battery quickly... i think asus laptops are not friendly when it comes to linux.

---

### Post by djwitkac on 2019-09-21
hi msrr18

Nothing fancy with installation Ubuntu at all. You need to disable secure boot just in case in bios. Then USB and should go fine.
Sometimes after installation I had issue with no HD detected either in bios and when run the OS first time. However switch off and on Laptop resolved that issue.
Now after installing yesterday new Ubuntu kernel 5.0.30x and today newest Kernel 5.3.1x however system couldn't log me on and was a kernel panic issue ;( when switched back to previous installed Kernel 5.0.29x all is good again. However will be discovering that issue cause on Linux Mint when upgraded to Kernel 5.2.x didn't had such problem. Probably again issue related to IOMMU which is f****ed in those laptops. Energy management related thing. Asus should make it fix for it . Just a newer bios or something....

---

