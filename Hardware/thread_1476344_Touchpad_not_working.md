---
title: "Touchpad not working"
date: 2010-05-07
forum: Hardware
---

### Post by Lurkos on 2010-05-07
I've reinstalled my system from Ubuntu 9.04 to 10.04 and I have various problem.
I've got an Acer 5920G.
One of them is the touchpad. It doesn't work!

Dmesg shows me this error
```
psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 5 bytes away.
```
that is probably related with this issue.

Moreover I've found that it is possible to use the Touchpad with:
```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=exps (or imps)
```
BUT scrolling and all the other features except that moving the arrow do not work.

I have to point out that everything worked perfectly with 9.04 out of the box.
Do you have any hints?

---

### Post by Lurkos on 2010-05-09
I've discovered that the touchpad works perfectly until the login screen (GDM) and stops working afterwards.
Do you have any suggestion to fix this problem?

---

### Post by P4man on 2010-05-09
I have the same laptop (acer aspire 5920G, the one with nvidia 8600 videocard) and no problems. You might want to update your bios, or try this workaround: add ```
i8042.nomux
``` to your kernel boot options.

---

### Post by Lurkos on 2010-05-09
Relevant dmesg output follows
> $ dmesg | grep -i touchpad
[   15.843017] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1e0b1, caps: 0xc04751/0xe0500f
[   15.879801] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio3/input/input10
[   16.514014] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x81a0b1, caps: 0xa04711/0xa04000
[   16.547467] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[   74.899314] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[   78.659082] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.


---

### Post by Lurkos on 2010-05-09
> **P4man said:**
> I have the same laptop (acer aspire 5920G, the one with nvidia 8600 videocard) and no problems. You might want to update your bios, or try this workaround: add ```
i8042.nomux
``` to your kernel boot options.

I have the 8600M GT video card.
Did you install the proprietary drivers? Just to understand which are the differences between our configurations.

---

### Post by P4man on 2010-05-09
yes I have the proprietary drivers, but I dont recall having any trouble before installing them.

My bios version is v1.3811

---

### Post by Lurkos on 2010-05-09
Another question: 32 bit or 64 bit?
I have the 64 bit version.

---

### Post by P4man on 2010-05-09
32 bit here.  (would have sworn I installed the 64 bit, but apparently not)

---

### Post by P4man on 2010-05-09
Do you have the problem in a live CD? If so, I could quickly make a 64 bit boot usb and try that. Meanwhile id still suggest you try the above workaround.

---

### Post by Lurkos on 2010-05-09
> **P4man said:**
> Do you have the problem in a live CD? If so, I could quickly make a 64 bit boot usb and try that. Meanwhile id still suggest you try the above workaround.

I've just tried the above workaround, but it doesn't work.
The strange thing is that until GDM the touchpad works.

EDIT:
Trying to go back to GDM (using "switch from"), enabling the touchpad with Fn+F7 and then going back to my user desktop seems to work.
It's really very strange.

---

### Post by P4man on 2010-05-09
Dont have the 64bit release version iso anymore; so I tried beta1 64 bit. Works fine. scrolling and everything and no weirdness in dmesg. 

Here is what I get
```

 28.131807] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x81a0b1, caps: 0xa04711/0xa04000
[   28.170114] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10

```

interestingly I dont seem to see any reference in lsusb or lspci

ubuntu@ubuntu:~$ lsusb
Bus 007 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
04:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Lurkos on 2010-05-09
I've found a way to reproduce the bug.

CASE 1:
+ start/reboot your computer
+ enable the touchpad in GDM login screen using Fn+F7
+ put your credentials and log into Gnome
The touchpad should work, but "randomly" stops working.
Even if sometimes it stops working, the GDM login screen is not affected by this block, because if I try to switch user, I can use the touchpad in the login screen.

CASE 2:
+ start/reboot your computer
+ disable the touchpad in GDM login screen using Fn+F7
+ put your credentials and log into Gnome
The touchpad should NOT work, even trying to enable it using Fn+F7.

The interesting thing is that in GDM it always work.
Do you have any idea of where can I find a log about this issue?
I would like to fix it soon, because touchpad is somewhat indispensable in a notebook...

---

### Post by P4man on 2010-05-10
I cant reproduce the problem here. I think that points to either:
- different hardware. while the product may have the same name there might be subtle differences (do you get the exact same touchpad model in your dmesg?)
- some software you installed (does the problem occur in livecd session for you?)
-bios or hardware


Here is what I found on your error message:
> 
Problem:
~~~~~~~~

I'm getting these:

	psmouse.c: PS/2 mouse at serio0 lost synchronization, throwing 2 bytes away.

Solution:
~~~~~~~~~

Check your mouse cable. If this only happens when you move your mouse in a
certain way, fix the mouse cable or replace the mouse.

Check your kernel and harddisk settings. This message can also happen when
the mouse interrupt is delayed more than one half of a second. Make sure DMA
is enabled for your harddrive and CD-ROM. Kill your ACPI/APM battery
monitoring applet. Try disabling ACPI, frequency scaling. Make sure your
time is ticking correctly, often with frequency scaling it gets unreliable.
Even if you're using the ACPI PM Timer as a clock source - actually this
often leads to the above problem. 


Maybe a stretch, but I had to replace my dvd drive on my acer, so its no longer the standard one. Since its also mentioned as a possible cause,  If all else fails, try removing it and see if it makes a difference?

---

### Post by Lurkos on 2010-05-11
Well... LiveCD works well.
I've also discovered that new user accounts are now affected by this issue.
I'm thinking it's a problem of my gnome configuration, but of course it's hard to understand where.
Probably the best option is to try to refresh my home directory.

---

### Post by Linfreak on 2010-06-09
I had the exact same problem as you had, on my Acer Aspire 5740. My laptop has a dedicated button that turns on/off the touchpad. When I actually saw that the touchpad wasn't working past the gdm login, I tried pressing it a couple of times but to no avail. One thing I noticed was the popup indication that came up each time I pressed it. It showed the reverse of what I actually did as in if I had enabled the touchpad it showed it as being disabled. I just went back to login screen and disabled the touchpad there. When I came back in and pressed the button, voila, touchpad worked like charm and this stayed that way even after rebooting. Do you by any chance  dual boot Ubuntu with any other OS? coz i suspect changes made there 'might' have something to do about the problem being reflected in Lucid. 

Cheers,
Siva

---

### Post by Spac3man on 2010-07-10
> **Lurkos said:**
> I've found a way to reproduce the bug.

CASE 1:
+ start/reboot your computer
+ enable the touchpad in GDM login screen using Fn+F7
+ put your credentials and log into Gnome
The touchpad should work, but "randomly" stops working.
Even if sometimes it stops working, the GDM login screen is not affected by this block, because if I try to switch user, I can use the touchpad in the login screen.

CASE 2:
+ start/reboot your computer
+ disable the touchpad in GDM login screen using Fn+F7
+ put your credentials and log into Gnome
The touchpad should NOT work, even trying to enable it using Fn+F7.

The interesting thing is that in GDM it always work.
Do you have any idea of where can I find a log about this issue?
I would like to fix it soon, because touchpad is somewhat indispensable in a notebook...

I am having the same problem as case 1.

---

