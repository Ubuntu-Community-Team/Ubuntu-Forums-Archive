---
title: "Mouse/Keyboard freeze during installation"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by Ug on 2009-01-27
I've just being trying to install Ubuntu 8.10 on my desktop i386 PC and I've hit a snag. Using the mouse I've been able to select a language or time zone and then the mouse and keyboard freeze.

The same is happening when running Ubuntu from the live-CD. After roughly 10 seconds of so, the mouse and keyboard just freeze. The computer becomes completely unresponsive and I have to turn the power off to the computer.

I've checked the CD and it's apparently fine. But this is quite mysterious. Windows XP is still running fine.

Any thoughts?

---

### Post by ajgreeny on 2009-01-27
Are they usb keyboard and mouse?  I seem to remember hearing about some problems with usb not being activated quick enough in certain hardware combinations, but can't remember much more than that.

---

### Post by Ug on 2009-01-27
Yes they are a USB keyboard and mouse. The keyboard, is via a wireless USB and the mouse is a wired USB connection.

I just attempted another install and I got further this time, to the disk partitioning stage but as I was editing the parameters it froze up.

---

### Post by ajgreeny on 2009-01-27
I suggest you at least try a non wireless version if not a different keyboard socket setup, and a ps2 mouse if the machine has a socket for it.  It may just allow you to install fully, and then try the wireless and/or usb items again.

---

### Post by Ug on 2009-01-27
Sadly I don't have a PS2 mouse or wired keyboard to try this out with. This is somewhat frustrating!

I've used the present mouse/keyboard combo right back to Fedora Core 1.

What's more curious is why this has suddenly happened. I'd fired up the liveCD several times in the days before, without any hiccups at all. And then all of a sudden... this comes along.

---

### Post by Ug on 2009-01-28
I went out and sourced a PS2 mouse and keyboard today. I also reburned the iso of Ubuntu 8.10 onto another CD-R.

I tried to install Ubuntu again, but experienced the same difficulties, of the machine just freezing up. But this time the problem is worse, now I can't even get into the live CD or beyond the wallpaper appearing on the installation process.

This is really grating!

Should I try an Ubuntu 8.4 install -- then upgrade? That doesn't strike me as a very elegant solution, but might be a viable option perhaps?

---

### Post by Ug on 2009-01-28
I've just booted up Fedora 10 to get some system info. From /sbin/lspci:

```
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 1a)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 9100 IGP
02:08.0 Ethernet controller: 3Com Corporation 3Com 3C920B-EMB-WNM Integrated Fast Ethernet Controller (rev 40)
02:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:0c.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
02:0c.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
03:00.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```

And from /sbin/lsusb:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

My machine is an old Intel Celeron CPU 2.80GHz. I hope that helps some?

---

### Post by Ug on 2009-01-29
For those with a similar problem. I've discovered that Ubuntu 8.04.2 installs with no problems whatsoever. I'll try and update the system later today, to see if the situation resolves.

---

### Post by Ug on 2009-01-29
I spent most of the day in the rather lovely Hardy Heron, or Ubuntu 8.04.2 LTS, which worked splendidly and was rather dreamy.

Then an hour or so ago -- I decided to take the plunge and see if I could upgrade to Ubuntu 8.10 successfully.

Alas. No such luck.

The system installed and then when it rebooted, I was presented by Grub with a choice of two kernels. The one which was automatically selected *kernel 2.6.27-11-generic* crashed during loading, and presented me with this error message a couple of times, that has left me completely baffled.

```

Alert! /dev/disk/by-uuid/4cf913c0-6214-404e-bb9a-baf92acfc1bo does not exist. Dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-lubuntu7) built in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs) _

```

So I rebooted and tried the other option, *kernel 2.6.24-23*. It was all going so swimmingly well, I'd even logged into the system, when all of a sudden... FREEZE. And I found myself back at square one when I first tried to install Ubuntu 8.10.

This is very, very frustrating. Can anyone recommend anything that I could perhaps try? Or should I revert to 8.04.2 LTS and just wait until Ubuntu 8.10 is less buggy, or perhaps even for 9.04?

---

### Post by Ug on 2009-01-30
Just for the record I've reverted to Ubuntu 8.04.2 for the present. But I value any further insight.

---

### Post by Mr_B on 2009-02-13
I had the same symptom. My problem turned out to be video driver problem. The system had worked great with 8.04 but when I did a fresh install of 8.10 it froze during boot. It is an older Pentium 4 motherboard with a build in Intel graphics chipset. I solved it by booting into recovery command line and editing /etc/X11/xorg.conf and changing the device to "VESA" instead of default - see below.
--original code--
Section "Device"
	Identifier	"Configured Video Device"
EndSection
--new code--
Section "Device"
	Identifier	"VESA"
EndSection

I hope it helps.

---

### Post by peikingd on 2009-02-14
I have exactly the same problem - although mine takes a while longer to freeze, I managed an install at least.

This seems to be a recurring problem, I will link to various threads I have seen - none of which helped me - but maybe you.

---

### Post by peikingd on 2009-02-14
See here [https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDell](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDell) I think my problem may be with using a dell dimension C521 without a usb hub.
I have seen a lot of "solutions"(none worked for me) based on placing commands like noapic acpi=off in boot. These all seem to have been suggested for earlier versions however.

---

