---
title: "[SOLVED] Ram still only showing 866M in htop/top/free"
date: 2008-08-01
forum: Hardware
---

### Post by the7erm on 2008-08-01
When I open up htop I only see 866M ram and in top it's 887572k ram

I found this post
[http://ubuntuforums.org/showthread.php?t=24969](http://ubuntuforums.org/showthread.php?t=24969) (it won't let me reply)

Followed the instructions: "sudo apt-get install linux-686 or in Synaptic search and install that."

Rebooted just to make sure, and poof still at 866M.

The only thing I can see doing is downloading an iso for a 686, and installing that.  Do I have any other options?

I only have 1024M of ram so I'm honestly wondering if it's even worth re-installing.  Everything is running fine.


```

$ free
             total       used       free     shared    buffers     cached
Mem:        887572     836032      51540          0      30568     242952
-/+ buffers/cache:     562512     325060
Swap:      2602488     503856    2098632

```


Erm

---

### Post by Fire_Chief on 2008-08-01
I'd guess your system is sharing the system RAM with the graphics card. Check your BIOS and see how much RAM is configured for the video settings.

If so, then you probably don't want to change it. This would behave the same in Windows as well so it's not an Ubuntu specific incident.

Cheers!

---

### Post by the7erm on 2008-08-01
I'm running an nvida card in a pci.  Although I'll check the bios just to be sure.

---

### Post by tamoneya on 2008-08-01
> **the7erm said:**
> I'm running an nvida card in a pci.  Although I'll check the bios just to be sure.

that doesnt necessarily mean it has its own ram.  Can we get a model number or some other stats on the card.

---

### Post by the7erm on 2008-08-01
Looks like it's a **GeForce FX5500**
```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
**02:03.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)**
02:04.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
02:04.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
```

---

### Post by tamoneya on 2008-08-01
> **the7erm said:**
> Looks like it's a **GeForce FX5500**
```
$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
**02:03.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)**
02:04.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
02:04.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
```

Hmm.  That card should have 128 MB to 256 MB of ram which should be sufficient for its needs.

EDIT: I just noticed that you also have a ATI RC410.  Im guessing this is integrated graphics and you appear not to be using it.  This would not have any ram and would be stealing from your system memory.

---

### Post by Fire_Chief on 2008-08-01
Okay, probably not the video card then. How many RAM sticks are in your system and what is the breakdown of capacities (i.e. 2x 512MB sticks, 4 256MB sticks, etc.)? Have you run a memtest lately to see if you have any bad RAM modules?

Also, please post the output of```
uname -a
```

Cheers!

---

### Post by evets25 on 2008-08-01
> **tamoneya said:**
> Hmm.  That card should have **128 MB to 256 MB** of ram which should be sufficient for its needs.

EDIT: I just noticed that you also have a ATI RC410.  Im guessing this is integrated graphics and you appear not to be using it.  This would not have any ram and would be stealing from your system memory.


No, it definately is the graphics card eating up your ram. With nvidia cards, the "FX" cards always use the shared memory, or whatever it is they are calling it now to make it sound less horrible than it really is. :D Also, you can tell from "128 MB to 256 MB". If you ever see a graphics card with memory like that, or it is described as having "up to" a certain amount of memory, you know it's sharing with your ram. 

This behavior can probably be configured in the bios.

---

### Post by Fire_Chief on 2008-08-01
Yup, I didn't see tamoneya's last edit and missed the other vga controller. Good catch you guys.

---

### Post by the7erm on 2008-08-02
Bummer ok, well thanks for the info/help.

Erm

---

