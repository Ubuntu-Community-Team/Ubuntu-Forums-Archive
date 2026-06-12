---
title: "wireless on Fujitsu seimens Amilo Li 1718 with ubuntu 9.10"
date: 2009-11-18
forum: Hardware
---

### Post by Cowboybebop79 on 2009-11-18
I have recently had to replace the hard disk on my Amilo which up till now had windows vista factory installed. I took this opportunity to test the viability of having Ubuntu on the machine instead. The main problem I have at the moment is getting the wireless up and running. I have done a bit of searching on Google and have found some references about madwifi and ath5k and ath9k drivers but the instructions are for Ubuntu 7.04 & 8.04 and I am not sure whether I can use the instructions on this site any more. 

[http://www.amilo-forum.com/topic,1029,-Li1718-auto-installation-for-ubuntu-32bit-Testers-needed.html](http://www.amilo-forum.com/topic,1029,-Li1718-auto-installation-for-ubuntu-32bit-Testers-needed.html)

Or whether there is an up-to-date method for doing this.

Any help is appreciated (don't make me go back to vista;))

---

### Post by hal10000 on 2009-11-18
Post the output of the commands
```
lspci
```
and ```
lshw -C network
``` to see if your wireless card is recognized by ubuntu

---

### Post by Cowboybebop79 on 2009-11-19
Hello Hal thanks for the quick reply I ran both of the commands in terminal and this is the output.

lspci Output:

```

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
0a:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

lshw -C network output:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:c0:a8:f4:e5:33
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:8e:fd:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.66 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:23 ioport:a000(size=256) memory:c0200000-c02000ff
```

I can see from the output that it is being detected but I know that the activation and deactivation of the wireless is controlled by a special non keyboard button which presumably would need to be detected before the wireless can be activated. But I am not an expert and I might be in completely the wrong ball park.

Hopefully I will be able to say that > I'm completely operational, and all my circuits are functioning perfectly

but until then I'm more of a 9000 series than a 10000

thanks again for any help in advance.

---

### Post by KaiJordanDay on 2009-11-20
I have the exact same problem. On previous ubuntu versions 8x and below, you could download smething to enable the wireless button. 

The wireless button is on like the powe button, which enables the wireless card. On Windows its set to auto-start but on ubuntu its non-responsive. Without this the internet cannot be started.

Fujitsu Siemens Li 1718.

(All fixes I had for previous versions, NO LONGER, work.

---

### Post by Cowboybebop79 on 2009-11-21
I have narrowed down my search for a solution to building the acerhk drivers. As far as I can see this is the only problem with getting things running smoothly. As a not I found the keyboard layout for Amilo laptops and all of the function keys work perfectly so I hope everything else will work perfectly when I find out how to build drivers from source. searching the forum as I type this.

---

### Post by Cowboybebop79 on 2009-11-26
Ok so wireless is working on my laptop and I'm a happy bunny. For any one who ends up here having the same problems these are the steps I used to get it up and running

1. I followed the steps outlined by Momo in this txt file

[http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt]("http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt")

2. Downloaded and installed Acerhk GUI and followed its steps to load acerhk.ko which was incredibly simple because it does it automaticaly

Hope this helps anyone with a similar problem. Just as a little bonus my laptop is 10 degrees cooler at least while running which means it will have a longer life expectancy. :D

---

### Post by arm-c on 2010-09-07
The recent acerhk gui program at the following link should take care of everything.  The acerhk source code is included and the program will compile from source if not detected and install it.  This is very handy because on kernel upgrades, you won't have to repeat the steps manually each time if there is a major shift in the kernel.

Link for download is: [http://sourceforge.net/projects/acerhkgui/](http://sourceforge.net/projects/acerhkgui/)

Also, please, please, please leave positive feedback on the project if you find it helpful.  I have only one comment and it is negative, which based on the number of downloads I get is not reflective of the usefulness. 

Also, the utility was tested by momo and he had it run flawlessly on his system (Amilio). Mine works great too (Acer C300 tablet).

v/r
ARM-C

---

