---
title: "Dell Mini 10 Sound Cuts Out?"
date: 2009-10-30
forum: Hardware
---

### Post by scout4536 on 2009-10-30
I have just recently done a clean install to 9.10.  Everything worked great.  Now whenever I boot I have sound, than about 15-20 minutes into a session my sound cuts out.  I have no clue what could be causing this.  I have all the updated kernels 2.6.31-14-generic.  Just need to know what could be causing this and a fix for it?  I don't understand how it could work at first, and then cut out like it does.  Any help would be greatly appreciated.

Found a fix that seems to be working now:

sudo nano /etc/modprobe.d/alsa-base.conf

deleted last line: options snd-hda-intel power_save=10 power_save_controller=N

and changed to: options snd-hda-intel model=dell

---

### Post by scout4536 on 2009-10-31
lspci

00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01

I followed this thread and still have the issue: [http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html](http://georgeblog.nyarangi.com/2009/10/no-sound-on-dell-mini-10-running-ubuntu.html)

It's just all audio stops when I restart, but if I do a complete shutdown and restart it works again, just a tad annoying.

Any ideas would be grateful....thx


Found a fix that seems to be working now:

sudo nano /etc/modprobe.d/alsa-base.conf

deleted last line: options snd-hda-intel power_save=10 power_save_controller=N

and changed to: options snd-hda-intel model=dell

---

