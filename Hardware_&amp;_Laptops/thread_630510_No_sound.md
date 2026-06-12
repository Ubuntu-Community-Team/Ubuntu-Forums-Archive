---
title: "No sound"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by Daniel0 on 2007-12-03
The sound doesn't work on my laptop (HP Pavilion dv9685eo) in 7.10 (32-bit). It seems to recognize my soundcard, but there is no sound. I've tried following [this topic](http://ubuntuforums.org/showthread.php?t=205449), but nothing worked.

lspci -v
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c4000000-c6ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Hewlett-Packard Company Unknown device 30cc
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00007fff
	Memory behind bridge: f4000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f3ffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30cc
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00008000-0000bfff
	Memory behind bridge: bc000000-bfffffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cbffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30cc
	Capabilities: [a0] Power Management version 2

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f8000000-f80fffff
	Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30cc
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f8404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
	Memory behind bridge: f8100000-f81fffff
	Capabilities: [50] Subsystem: Hewlett-Packard Company Unknown device 30cc

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 18d8 [size=8]
	I/O ports at 18cc [size=4]
	I/O ports at 18d0 [size=8]
	I/O ports at 18c8 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f8404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: medium devsel, IRQ 10
	Memory at 88100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1) (prog-if 00 [VGA])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 135c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [c8] Power Management version 2
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [e0] Express Legacy Endpoint IRQ 0

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at c000 [size=256]
	Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [60] Express Endpoint IRQ 0
	Capabilities: [84] Vendor Specific Information

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2

07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f8100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f8101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f8101400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I'm not sure what what other kind of information that could be useful. I hope somebody can help me.

---

### Post by linuxwizard on 2007-12-04
Check over see if your computer falls into this group.

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by Daniel0 on 2007-12-06
I suppose you could consider my computer an HP Pavilion dv9000 series. I've tried the methods in the link you provided but unfortunately none of them worked. Still the same problem. It recognizes my card fine, but there is no sound.

---

### Post by vikramsharma on 2007-12-06
Are you using internal speakers of the computer, in case you are that might be the problem.  Try connecting headphone or speaker to the headphone jack on your computer and see it there is any sound.  I have a Lenovo system at office and it has/had this problem I cannot get the internal speakers to work but the headphone work fine for me.

---

### Post by Daniel0 on 2007-12-06
Doesn't work with either :(

---

### Post by adamleander on 2007-12-06
I'm having a some what similar issue.  The card is detected, however I do have the first two sounds.  The default sound from the log on screen, and the default sound Ubuntu plays when it loads work fine.  Just I have nothing after that and can't for the life of me figure out why.

---

### Post by bmwman91 on 2007-12-06
I just got started with Mint 4.0 (Gutsy with extra junk for noobs like me).

After the install the sound worked fine.  The wireless had some real issues, but sound and other things worked.

So, I used the included package update manager to update all my packages.  Wireless started working, my ATI FireGL card started working properly, etc.  However, the sound no longer does.

The laptop is a Thinkpad T41p which uses an Intel 82801DB sound card (integrated).  I have gone through every one of the audio troubleshooters I could find on here, and nothign seems to fix it.  The hardware is recognized, and the drivers are all loaded.  I can go into Amarok and play audio files with the visualizer going properly, but no sound comes from the speakers or headphones.  I checked alsamixer and turned off the external amp, but to no avail.  Even adding the ac97_quirk bit into the alsa-base file.

So, has anyone figured out WTF is going on?  I really, REALLY do not want to have to dual boot with Windows.  I have used Windows for a long time, and really do not want to have to anymore lol.

Thanks.

---

### Post by Yellow Pasque on 2007-12-06
> **bmwman91 said:**
> II really, REALLY do not want to have to dual boot with Windows.  I have used Windows for a long time, and really do not want to have to anymore lol. Thanks.

Before you stoop so low, give OSSv4 a shot (see my sig).

---

### Post by bmwman91 on 2007-12-06
Thanks for that.  I will give it a try when i get hom efrom work (there is only so much non-work I can do at work!).

What exactly are the differences between OSS and the Alsa drivers/resources?

Is Alsa just inherently buggy with a lot of Intel audio stuff?  Google searches bring up a lot of issues (many similar to mine, none with applicable fixes).

This is my first time with Linux, and Mint 4.0 is the first distro I have actually installed.  I booted from the Mandriva 2008 LiveCD, and was just not as impressed, and the whole paying to upgrade to the "full" version did not sit right with me based upon my initial impression of Linux's "mission."

I want to give this an earnest try, and am aware that the endless hardware bugs I keep running into can be solved quickly in the future (at the expense of hours of searching now).  I am also aware that hardware setup on my Thinkpad went a hell of a lot more smoothly on Windows (blasphemy, I know), not because Windows is "better", but because IBM designed the product and all the drivers to be run on Windows.  This OS swap was never had my expectations aimed at seamlessness, but there comes a point where I just want a PC that works without having to fight fires every time I boot.  I honestly hope that I can get this working 100% because many of Linux's merits are quite obvious.

I have also noticed a very...interesting dynamic among software enthusiasts.  I am a mechanical engineer by profession, and do not interact with a lot of software folks.  Flame wars on software forums sure are easy to start though!  I guess software is a very personal thing to many.

---

### Post by Sutur on 2007-12-06
Try the older ALSA drivers/backported modules.

My girlfriend has an HP 6500 which didn't have working sound until we did that. Probably uses the same soundcard.

```
sudo apt-get install linux-backports-modules
```

---

### Post by bmwman91 on 2007-12-06
> **Temüjin said:**
> Before you stoop so low, give OSSv4 a shot (see my sig).

Here is the brick wall I am running into.  I would love to try out OSS drivers, if only I could get them to install.

```
twinion@twinion-laptop:~/Desktop$ sudo dpkg -i oss-linux_v4.0-1009_i386.deb
(Reading database ... 91072 files and directories currently installed.)
Preparing to replace oss-linux v4.0-1009 (using oss-linux_v4.0-1009_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux_v4.0-1009_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux_v4.0-1009_i386.deb
twinion@twinion-laptop:~/Desktop$ ossxmix
/dev/mixer: No such file or directory

```

---

### Post by bmwman91 on 2007-12-06
> **Sutur said:**
> Try the older ALSA drivers/backported modules.

My girlfriend has an HP 6500 which didn't have working sound until we did that. Probably uses the same soundcard.

```
sudo apt-get install linux-backports-modules
```

I tried it, but no luck.  Thanks though!

---

### Post by Yellow Pasque on 2007-12-06
Apparently, I've led you astray and _assumed_ you had basic software building packages. Indeed, I've made an _***_ out of _u_ and _me_ and for that I apologize.
Folllow these instructions (except for the last one). 
[http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

Now run the following command to get the necessary packages and try again:
```
sudo apt-get install gcc make build-essential binutils linux-headers-`uname -r`
```

---

### Post by bmwman91 on 2007-12-07
Well, thanks for the heads up on the compiler.  I will install it for the sake of having it as I will likely need it in future Linux adventures.

I reinstalled Mint and ran all the updates in the update manager.  Everything works way better than before.  My first time through, I tried a couple stupid ATI driver things which caused issues all over.  I also messed with Compiz and that seems to be one of the roots to all my issues.

So, a clean reinstall and avoiding installing stuff I do not yet understand 100% has fixed my problems.  yay.

---

