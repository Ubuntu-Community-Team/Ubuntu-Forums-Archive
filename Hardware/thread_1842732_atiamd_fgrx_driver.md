---
title: "ati/amd fgrx driver"
date: 2011-09-12
forum: Hardware
---

### Post by ilantal on 2011-09-12
I am loading ubuntu 64 bit on a friend's HP Pavilion dv6 with 4 CPUs and 4GB memory - a very nice computer.
Things went smoothly until I decided to activate the restricted display driver. After reboot it decided that the computer wasn't good enough to run unity and went into Ubuntu Classic mode. This is of course nonsense, as the computer is better than anything I have and all my machines are running unity.
I removed the restricted driver and unity came back. Then I activated the driver again and unity went away.
Is this a known bug, or is there a way I can convince the driver that the machine really is capable of running unity?

Thanks,
Ilan

---

### Post by Jagoly on 2011-09-12
well, I have a HP pav DV6 with a quad core cpu and 4 gigs of memory, and I never had such problems. So you're say that when you use additional drivers to install fglrx, you get this problem, but when you use the radeon drivers, it works? hmmm... strange.

would you be able to post the output of pciconfig? or if you know what the model of the laptop is that would work too. it may be the excact sames laptop as mine, or it may be the newer model. mine has a first gen i7 1.6 ghz cpu. that should be a good indication.

---

### Post by ilantal on 2011-09-12
Thanks for the reply. Sorry but I don't know what pciconfig is and the terminal doesn't recognize it either. I also don't know where to pick up the model number. I went to System Monitor and that reports 3.7 GiB and 4 Intel Core i5 CPU M450 @ 2.40GHz. The kernel is 2.6.38-8-generic.
If you have i7, that sounds better than my i5?

In any case it is 100% repeatable - if I use the restricted driver, no unity and without it, all is well. I've never seen such a thing.

The first time around it told me my hardware wasn't good enough to support unity and after that it simply doesn't use it. It told me once and isn't a nudnick. I would like to convince it to look again and tell me what it thinks is wrong.

Ilan

---

### Post by Jagoly on 2011-09-12
](*,)

pciconfig??? I'm getting my commands mixed up, I meant "lspci". Either way, I think I've determined what the laptop is. It's probably a HP 3070TX. That's exactly the same as my laptop, but the CPU is one step down and the hard drive is slightly smaller.

Problem is, the gpu is an ATI Radeon 5650, which is exactly the same gpu as my laptop, which runs unity great with the fglrx drivers. So I have no idea why it isn't working. I suppose you could try the latest drivers from amd's website.

Sorry I couldn't be of more help :-(

---

### Post by ilantal on 2011-09-12
In any case I very much appreciate your answers. How did you figure out the size of the disk? It is 500GB but how could you know? Running the command gave:
matan@matan-HP:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
matan@matan-HP:~$ 

I noticed that it hadn't done updates, so I ran it through the latest updates. Still no improvement.

There is something which worries me about this machine. After doing a reboot on removing the driver it hung before getting to the login screen. That is NASTY. Maybe there really is something wrong with it.

I decided that it is safer with the restricted driver, so I installed Unity-2D. Clearly the 2D version works. What blew me away is when I use the restricted driver, now instead of Ubuntu Classic it gives me Ubuntu-2D (when I ask for Ubuntu). It seems to remember the last step down from Unity which I used. All very strange, so I'll keep an eye on it.

Thanks again,
Ilan

---

### Post by .... on 2011-09-12
You have Intel and ATI (i.e. hybrid) graphics, and the Intel GPU is used by default unless you have a BIOS switch to disable it or you use the vgaswitcheroo script (which only works with opensource drivers). Make sure you remove all traces of the proprietary ATI driver as it's not going to work. Run the 6 commands here (the first one may not work, that's okay): [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

