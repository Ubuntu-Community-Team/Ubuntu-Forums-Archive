---
title: "8800M GTS Lock Up"
date: 2013-01-24
forum: Hardware
---

### Post by Parismessios3 on 2013-01-24
Hello, I have a laptop which has the 8800M gts. I am trying to completely delete windows in order to have only ubuntu on my system. However, when I install nvidia drivers, the laptop freezes completely (keyboard, mouse, everything) a few seconds after login. I tried everything that I found on the internet, and I installed the latest drivers. The same result. Somebody recommends to install drivers version 295.20 in such cases, but when I try to do, I get an error that it cannot find version.h.
Can anybody help me?
I am using ubuntu 12.10

---

### Post by typhoon_tip on 2013-01-25
Post the output of:
```
lspci
```

Thanks.

---

### Post by Parismessios3 on 2013-01-25
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce 8800M GTS] (rev a2)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Mass storage controller: Silicon Image, Inc. SiI 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
0c:06.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 70)

```

---

### Post by typhoon_tip on 2013-01-28
All looks fine, and no dual VGA to deal with.

Just a suggestion to try, after a problem that I have run into as well (with similar outcome as you).

Install the drivers using the following method (make sure is all purged well before trying !):

```

sudo apt-get install nvidia-current
sudo nvidia-xconfig

```

Then reboot. Very very important, do not reboot before executing the nvidia-xconfig command. Sometimes it happened to me the wrong X file was created after installation of NVIDIA drivers, and nothing would work. Just making the proper file would solve the problem for me.

Try and report back.

---

### Post by Parismessios3 on 2013-02-06
Ok, I have done that, but now my laptop cannot change resolution, it is at 800*600, and unity doesn't seem to load

EDIT: I followed the instructions from [http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/](http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/) in order to get unity back, and now laptop locks up again

---

### Post by phthano on 2013-02-07
> **Parismessios3 said:**
> Ok, I have done that, but now my laptop cannot change resolution, it is at 800*600, and unity doesn't seem to load

EDIT: I followed the instructions from [http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/](http://techhamlet.com/2012/11/install-nvidia-drivers-in-ubuntu-12-10/) in order to get unity back, and now laptop locks up again

Sounds like your composition isn't working. Can you load Ubuntu 2D?

---

### Post by Parismessios3 on 2013-02-07
Do you mean Unity 2D? 
Something that I forgot to tell is that when I am trying to install nvidia-current, on the terminal I get something like Debug: trying to match Lenovo T420 and fails (I don't have a lenovo)

EDIT: I used the advice here ([https://forums.geforce.com/default/topic/505391/8800m-gts-linux-freeze/](https://forums.geforce.com/default/topic/505391/8800m-gts-linux-freeze/)) and it is working perfectly, but is there any better solution?
As I understand, when the GPU tries to go to performance level 0, the laptop freezes

---

### Post by Parismessios3 on 2013-02-08
Does anybody know how to disable powermizer's performance level 0 ONLY?

---

