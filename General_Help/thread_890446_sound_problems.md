---
title: "sound problems"
date: 2008-08-15
forum: General Help
---

### Post by Drone4four on 2008-08-15
First my 10 or so media players can't play mp3s.  I don't see monoscope visualizations and the progress bar is stuck for every mp3 or .mpg I try to play.  Then I reboot Ubuntu and my media players play mp3s just fine, but YouTube doesn't play audio. So I reboot Ubuntu again and YouTube  plays audio but Amarok, Totem, et al don't.

How can I better describe my problem so I can search Google with more than just the useless 'ubuntu sound problems'?

Could this be a problem with PulseAudio?  I checked the PulseAudio FAQ.  [Here]("http://www.pulseaudio.org/wiki/FAQ#Troubleshooting") is the troubleshooting section.  Although it doesn't mention irregular sound problems.

---

### Post by Crafty Kisses on 2008-08-15
It could be a problem with Pulse, but post these outputs:
```
lspci
```
Then:
```
lsusb
```

---

### Post by Drone4four on 2008-08-15
```

daniel@ubuntu:~$ lspci
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
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
daniel@ubuntu:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 0d62:001c Darfon Electronics Corp. 
Bus 003 Device 002: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
daniel@ubuntu:~$ 

```

---

### Post by Drone4four on 2008-08-15
Can a mod please move this thread to a more appropriate subforum, like _[Multimedia and Video]("http://ubuntuforums.org/forumdisplay.php?f=334")_ where it should get more appropriate attention?

---

### Post by Drone4four on 2008-08-16
When I make some time in my busy schedule this weekend, I will be back to troubleshoot my audio problem using _[these]("https://help.ubuntu.com/community/DebuggingSoundProblemsMisc")_ _[two]("https://help.ubuntu.com/community/SoundTroubleshooting")_ spectacular guides I found.


[This]("http://ubuntuforums.org/showthread.php?t=769850") might come in handy too.

---

