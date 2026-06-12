---
title: "Realtek not detected"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by ugarth on 2006-03-19
Hi, I've just acquired a brand new laptop, a asus A6 with a "Realtek RTL8168/8111 PCI-E Gigabit Ethernet NIC" and a "Intel Pro Wireless 3945ABG" as they report. Sadly, when installing Ubuntu doesn't detect any of my network hardware. Well I though, I install the drivers later and see if it works. For what it seems there aren't drivers for my wireless chipset, although I've read at intel's that a release should be expected early this year. Yes I know I can use ndis-wrapper, but I'll try that later.

My first step is to enable my ethernet card. I went to realtek webpage and downloaded the drivers, installed them, and nothing. Restarted the pc, tried to install them again, and still nothing. What I'm i doing wrong ? I'm new to Linux, and so far I'm liking.
[http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=8168](http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=8168)
[http://support.intel.com/support/notebook/sb/CS-006408.htm](http://support.intel.com/support/notebook/sb/CS-006408.htm)

note: after installing ubuntu froze when trying to startup the hotplug system, so I disabled it. I added a entry in /etc/hotplug/blacklist for snd-hda-intel, following these instructions
[http://www.nabble.com/Re:-hangs-on-%22starting-hotplug-subsystem%22-p2300638.html](http://www.nabble.com/Re:-hangs-on-%22starting-hotplug-subsystem%22-p2300638.html)
but I need the network up to complete those instructions.

---

### Post by ugarth on 2006-03-21
Please, help ! I can't networking to work on my system.

---

### Post by al108 on 2006-03-22
Also read this thread [http://www.ubuntuforums.org/showthread.php?t=143982](http://www.ubuntuforums.org/showthread.php?t=143982)
it's about rtl8169, but it's using same r1000 driver from Realtek.
Can you post your "lspci" and "dmesg | grep eth" outputs? Are you using win on this laptop? I assume that the card works there.

Alex

---

### Post by ugarth on 2006-03-22
Yes I have windows otherwise currently the laptop would be of no use for me. I'd like to start using Ubuntu extensively for my work and leave windows for leisure. in windows it works well.

lspci -n lists somehting like```
000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.: Unknown device 8168 (rev 01)
  Subsystem: Asustek Computer, Inc.: Unknown device 11f5
  Flags: bus master, fast devsel, latency 0, IRQ 11
  I/O ports at c800 [size=256]
  Memory at fe0ff000 (64-bit, non-prefetchable) [size=4K]
  Expansion ROM at f3030000[disabled] [size=64K]
  Capabilities: [40] Power Management version 2
  Capabilities: [48] Vital Product Data
  Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable-
  Capabilities: [60] #10 [0001]
  Capabilities: [84] #09 [014c]
```
dmesg | grep eth shows nothing.

---

### Post by al108 on 2006-03-24
Well, that output looks like ubuntu kernel driver for Realtek is not compatible with 8168 or there's some conflict with other devices. Did you try installing Realtek drivers? It comes with a readme that will outline steps on how to compile new drivers, you will need to install additional packages for it to work ie gcc-3.4, kernel headers, kernel tree, build-essential, maybe some other stuff too. When you run it and if it is missing anything it'll let you know - just install that missing package using synaptic or apt. Ohterwise installation went pretty smooth for me.

Good luck

---

### Post by ugarth on 2006-03-26
hum, I did install the drivers, followed the instructions, but I didn't have gcc-3.4, so I simply renamed my regular gcc (version 4) to gcc-3.4 .
Shouldn't this work ? It seems it doesn't.

---

### Post by al108 on 2006-03-26
Normally you don't rename your gcc, you can install gcc-3.4 in synaptic and you can have both gcc-3.4 and 4.0 installed at the same time. If I remember correctly realtek installer will not requier additional commands, while others like nVidia driver installer will require you to set environment like that 
```
CC = gcc-3.4
export CC
```
This will tell compiler to use gcc-3.4 as a default version. It is possible to use gcc-4.0 sometimes, but current Ubuntu kernels were compiled with gcc-3.4 and it's better to do just that.
I would recompile your drivers again and see what happens after that. After that  you can follow troubleshooting from here [http://www.ubuntuforums.org/showthread.php?t=143982](http://www.ubuntuforums.org/showthread.php?t=143982)
Of course you don't have to recompile your intrd unless everything else fails.
If your drivers are still not grabbing your card, try going into BIOS and resetting PCI configuration data - sometimes that help to shake things up.
Also you can try using Live CD maybe even Dapper to see if your rtl8168 will work there. Though Dapper is not officially reliazed it works for many without a problem

---

### Post by ugarth on 2006-03-27
Ok thank you.
I downloaded and installed gcc-3.4 and the problem presists.
A friend of mine also told me about the latest ubuntu test release, but I'm not willing to try test software.

---

### Post by al108 on 2006-03-27
Ok. So what you saying is r1000.ko compiled without a problem or did you have any messages other than OK from the compiler? Is r1000.ko in  ```
/lib/modules/`uname -r`/kernel/drivers/net/
``` directory? Did you do ```
sudo depmod -a
``` and was it successfull?, did you add r1000 into a ```
/etc/modules
``` file? Did you try to recompile your initrd without r8169 module as it could conflict with r1000? Did you try to reset your PCI configuration in BIOS? What is the output now of your ```
# lsmod | grep r1000
``` or ```
dmesg | grep eth
``` or lspci? Also look here for more troubleshooting info [http://ubuntuforums.org/showthread.php?t=142716](http://ubuntuforums.org/showthread.php?t=142716)

Did you check your CD media for errors? Did you try any Live CDs? It doesn't hurt to try Dapper Live CD since it doesn't install anything on your hard drive.
Don't be shy and describe in more details what exactly you are doing step by step and maybe more people would be willing to help you - it's really hard to go just from " it didn't work...", besides if you are successfull other people with similar problems will be able to find your thread and learn from it and know exactly what to do in their situation.

Cheers
Alex

---

### Post by ugarth on 2006-03-29
I managed to get the ethernet working.
the r1000 module was loaded. I simply did then a /etc/init.d/networking start and it worked.
But a new problem came along.
Ubuntu packet manager updated several drivers and the kernel, which erased the r1000 module. So I tried to build the module again, but make simply fails with the exact same files - this seems a regression with make. It can't match a rule, which is the 1st in the file. Which make version comes with ubuntu 5.10 by default  I might try to overwrite it.

Yet, the previous kernel is still working fine and the drivers is loaded, so I'll use this one.
Thanks !

---

### Post by al108 on 2006-03-29
I'm glad that you've finally got it working! I can't be sure of the make version that comes with ubuntu - just like you I do all the updates. The good part is you can uninstall the latest version and install the older one back if it is just the "make" problem. Actully I think I recall reading something that there could be a problem with the latest make but I may be wrong. 

Upgrading to a new kernel - if you don't see a big performance difference (and most people won't) or some special feature that is only available with new update (like switching to an SMP kernel) it's not necessary to upgrade it, besides if you have customizations - you will have to recompile them again everytime there is an update and they come out pretty often.

I've came across an interesting utility "modconf" that will let you manage which modules will be loaded at startup looks pretty cool. Be careful if you will use it though.

Cheers.

---

### Post by nanux on 2006-12-02
Hallo,
i have problem with same NIC. I have installed the r1000 module (compile,install,modprobe - used this tutorial [http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)) and lsmod list r1000 module.
When i enter "sudo /etc/init.d/networking restart" it dont get any dhcpoffer so it isn't been configured properly. Where can be problem? Thanks a lot.

Specs:
Ubuntu 6.10
laptop Asus V1J
kernel 2.6.17
network card Realtek 8168

---

### Post by figo2476 on 2007-07-24
Hi:

* Kubuntu dapper, kernel 2.6.x
* using realtek rtl8168
* download the driver from realtek, but when I 'make install' there is no 8168.ko....
* any hint....

thx in advance

---

### Post by figo2476 on 2007-07-24
> **figo2476 said:**
> Hi:

* Kubuntu dapper, kernel 2.6.x
* using realtek rtl8168
* download the driver from realtek, but when I 'make install' there is no 8168.ko....
* any hint....

thx in advance

Indeed, I find r8169.ko, but not r8168.ko. I assume change the name of the file won't work & it should not be a  good idea

---

### Post by Chemical22 on 2007-07-25
edit

---

