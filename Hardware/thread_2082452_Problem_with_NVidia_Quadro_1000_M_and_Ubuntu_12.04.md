---
title: "Problem with NVidia Quadro 1000 M and Ubuntu 12.04[64-bit]"
date: 2012-11-09
forum: Hardware
---

### Post by underdog012 on 2012-11-09
Hello everyone,


A couple days ago I was trying to connect my Lenovo W520 with my TV using the VGA port.My laptop is a NVidia Optimus Laptop.At first,I though that the VGA port was being manipulated by the Intel card.So,I went to the BIOS settings and I changed the Display settings by choosing the NVidia Optimus to work and let the laptop check if the OS is compatible with the Optimus technology or not. So I tried a couple of times but I wasn't able to see anything to my T.V.


After changing the BIOS settings again to Discrete graphics only without letting the laptop to check if the OS is compatible with the Optimus Technology,I tested it under Windows 7 and it seems  that the VGA port is being used only by the NVidia graphics card and not  the Intel card.I changed to Ubuntu and it booted and I managed to  connect my laptop with my TV,but unfortunately after I rebooted(only  with the NVidia card) Ubuntu didn't start at all.By the way I changed  then to Intel's graphics card and Ubuntu was able to boot again,but it  seems that the problem was only when the chosen video card was the  NVidia only.So I ran Ubuntu on recovery mode and I chose some of the  options there like the option which repairs broken packages,the grub  update,clean unnecessary packages,check files,etc.... and Ubuntu is  now able again to boot with the Nvidia card again only.Any ideas,why  this is happening?
  

My Nvidia card is the Quadro 1000M and the driver's version is the 295.40.
  



P.S.: Notice that I didn't press the "Save Configuration File" in the NVidia X Server Settings program,because I have heard that this option causes a lot of problem.I also had a bad personal experience with this,so I avoid to choose that specific option.:)

---

### Post by underdog012 on 2012-11-11
Please help me![-o<:sad::sad:

---

