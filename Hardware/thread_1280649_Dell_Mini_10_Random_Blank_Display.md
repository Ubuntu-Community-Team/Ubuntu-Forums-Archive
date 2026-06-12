---
title: "Dell Mini 10 Random Blank Display"
date: 2009-10-02
forum: Hardware
---

### Post by samurailink3 on 2009-10-02
When using my mini 10 with Ubuntu 9.04, on occasion the screen will shut off for no particular reason and refuse to come back on. Restarting X does not help. I can, however, get to tty1-6 and these display just fine. I've tried going to init 1 then back to init 5, but this doesn't seem to help. The only solution I've found is a full system restart. I've tried kernels -14 and -15, but both of these have the same issue. Everything else seems to be working perfectly, but this display is killing me. Any ideas?


uname -a: 
```
Linux Macaroni 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
```

lspci: 
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03) 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01) 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

lsusb: 
```
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device Bus 001 Device 002: ID 064e:a129 Suyin Corp. Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by snowishberlin on 2009-10-11
I have the exact same problem on a Lenovo 3000 N100 with a 9.04 fresh install.  It is not exactly that the screen shuts down, but is blank and black and unresponsive.  I can get to ttys and all, just like you, so it is not a malfunctioning display.  I have played with the screen saver and screen blanking tools and nothing helped.  I have the same GPU and general specs you do.  And I have no answer.
The display was fine from 7.04-8.10, and when I decided to buy a new hard drive and freshly install 9.04, this started.  I have tried many solutions, and also trying to get up to a higher resolution, but nothing.
Have you found anything to fix this?
I have the same GPU and general specs you do.  And I have no answer.

---

### Post by samurailink3 on 2009-10-11
I do believe I have found what was causing the issue. I went ahead and disabled the Intel Speedstep technology (for dynamically altering processor speeds for power-saving), and its been stable ever since. I noticed that the screen would blank shortly after a lot of up and down-shifting with the processor. Killed speedstep, which also hurt battery life, and the thing's been as stable as a standard linux box.

---

### Post by snowishberlin on 2009-10-13
Hi Samurai,
  I am not sure how to disable speedstep.  I looked for it elsewhere in the forum and found some stuff about editing the BIOS, or adding a CPU Frequency Monitor to the panel.  I added the monitor and set it to 'performance', but after a few hours... poof.  Another black screen.  I checked in Synaptic and I don't have the speedstep stuff installed.  Do I need to edit my BIOS?  How did you do that exactly?
Thanks!

---

### Post by samurailink3 on 2009-10-14
Yea, it would be located in your BIOS settings. Jam on F2 when you boot the machine. I don't have mine in front of me, but it should be located in there.

---

