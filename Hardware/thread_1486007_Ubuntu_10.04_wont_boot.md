---
title: "Ubuntu 10.04 wont boot"
date: 2010-05-17
forum: Hardware
---

### Post by mErchamion on 2010-05-17
I have recently acquired a Toshiba Satellite L500-ST5507:
Intel I5 430 Processor, DDR3 memory, Intel Integrated Graphics, Intel 5   series 4 port SATA AHCI Controller, Realtek RTL 8191SE Wireless LAN,   Intel 5 series/3400 series Chipset family USB Enhanced Host controller   3B34.
In this laptop, I have been able to boot ubuntu 9.01, though i couldnt   get the wireless to work (among other things). 

Now, I wanted to try Ubuntu 10.04, but I find that I can not even boot   the computer. When I boot from the live cd, I can see the menu screen,   but when I choose the "try without installing" option, all I get is a   screen full of weird messages, the last two of them are:

[0.600438][<c0104087>] kernel_thread_helper + 0x7/0x10
[0.600375][<c07a3308>] kernel_init + 0x0/0xbf
I tried wubi installation, but the same screen comes up when rebooting. 

After some suggestions, I checked for bios settings for  SATA controllers, but no change on this settings worked. I also run md5sum on the downloaded iso image and I got a result included in the  Ubuntu Hashes page. 

I was successful in installing Ubuntu 10.04 in a Virtual Box machine  with this live CD.

I will be very thankful if anybody can explain me what the problem is  and if there is a way to solve this issue. Waiting for your response!

---

### Post by mErchamion on 2010-11-28
Hello everybody. Nobody answered me here, but after a lot of research for the newbie I am, I have found a rather easy solution here:
[http://homeport.org/~bcordes/satellite-l500-install.html]("http://homeport.org/%7Ebcordes/satellite-l500-install.html")
If you get here trying to solve  a similar problem, just read what is said there and also here:
[https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way](https://help.ubuntu.com/community/Kernel/Compile#Alternate%20Build%20Method:%20The%20Old-Fashioned%20Debian%20Way)
and you will surely be able to patch, compile and install your fully functional kernel for toshiba laptops.
I have done so for 2.6.35 kernel in maverik. My L500 is working flawlessly, including battery meter, frequency scaling, fn's , suspend, etc. 

Thankyou all for your time.

---

