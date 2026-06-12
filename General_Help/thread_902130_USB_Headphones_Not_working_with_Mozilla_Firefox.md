---
title: "USB Headphones Not working with Mozilla Firefox"
date: 2008-08-27
forum: General Help
---

### Post by NeoAndersen on 2008-08-27
Hello!!

When I connect my Satellite USB headphones I must choose among 8 devices options in the Volume Control panel to make it work properly so I can listen my mp3 and video from my HD... But frequently I must disconnect and reconnect it again until it's recognized properly... But I never managed to make it work with sites streaming videos and music on the net like youtube and lastfm...  

How can I get my headphones working properly with Mozilla Firefox?
What is the logic behind the 8 devices in my Volume Control Panel?

---

### Post by Crafty Kisses on 2008-08-27
Post the results of > lspci

---

### Post by NeoAndersen on 2008-08-27
neoandersen@neoandersen-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
05:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
neoandersen@neoandersen-desktop:~$

---

### Post by markbuntu on 2008-08-28
What are the System/Preferences/Sound set to?
If they are on autodetect you can change them to alsa and then what you choose in the Volume Control should be used by all your applications.

Most of those devices are virtual devices that can be used by your sound server(s) and applications if you can figure out how to do that. 

I have 17 devices. 4 hardware devices and 13 virtual devices. I actually use 11 of them. But then again, I am sort of a fanatic about my sound. You can look at my crazy fanatical longwinded sound guide if you have a few spare hours:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by NeoAndersen on 2008-08-29
I've tried auto detect and alsa but no one worked... And now just "USB audio" option can make my headphones work as before but not with Mozilla Firefox...
I guess Ubuntu don't recognized the headphones properly or with the right drive... Can that be?

---

### Post by markbuntu on 2008-08-29
You should really read my guide.

---

