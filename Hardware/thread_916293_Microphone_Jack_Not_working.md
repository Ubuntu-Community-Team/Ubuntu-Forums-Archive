---
title: "Microphone Jack Not working"
date: 2008-09-10
forum: Hardware
---

### Post by CCX on 2008-09-10
Hello,

I installed ubuntu 8.04 on my Fujitsu Tablet PC T4220 about an hour ago and have been hunting for solutions to this problem since then:
My headphone jack doesn't work. I plug the headphone in but nothing happens. Sound continues coming through the speakers. 

I googled the problem but apparently there are solutions posted mostly for ubuntu 7.04 that I have found. I would like if someone can help me out here.

I'm pretty much frustrated and therefore, sorry if I didn't post the thread in the right section. If I have please tell me and I'll PM a moderator to do so. 

Thank you in advance for any helpers.

---

### Post by Bruce1940 on 2008-09-10
> **CCX said:**
> Hello,

I installed ubuntu 8.04 on my Fujitsu Tablet PC T4220 about an hour ago and have been hunting for solutions to this problem since then:
My headphone jack doesn't work. I plug the headphone in but nothing happens. Sound continues coming through the speakers. 

I googled the problem but apparently there are solutions posted mostly for ubuntu 7.04 that I have found. I would like if someone can help me out here.

I'm pretty much frustrated and therefore, sorry if I didn't post the thread in the right section. If I have please tell me and I'll PM a moderator to do so. 

Thank you in advance for any helpers.



Hello CCX.  I am having the same problem that you describe and came to this forum for that reason.  So, if you get an answer I will too.  Thanks. Good luck.

---

### Post by CCX on 2008-09-10
Dude, maybe we should PM an admin/mod and ask instead of doing this in a thread...

---

### Post by Crafty Kisses on 2008-09-10
I'd like to see the results of this command:
```
lspci
```

---

### Post by CCX on 2008-09-10
> **Codename said:**
> I'd like to see the results of this command:
```
lspci
```
I didn't get what it said at all :(

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
1c:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.1 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
1c:03.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)


---

### Post by SergeantScar on 2008-09-16
I am having the same problem. I have been looking around and I think that it has to do with the audio device. Intel Corporation 82801H (ICH8) HD Audio Controller. 

I have yet to find a solution..

---

### Post by SergeantScar on 2008-09-16
Actually check here:
[http://ubuntuforums.org/showthread.php?t=903926&highlight=82801H+(ICH8+Family)+HD+Audio+Controller]("http://ubuntuforums.org/showthread.php?t=903926&highlight=82801H+(ICH8+Family)+HD+Audio+Controller")

---

