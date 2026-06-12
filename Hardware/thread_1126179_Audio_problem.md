---
title: "Audio problem"
date: 2009-04-15
forum: Hardware
---

### Post by MartinoM on 2009-04-15
Hi! I have a little problem.. 10 days ago i have installed on my notebook (Acer Aspire 7720g) the drivers for dial-up modem (hsfmodem) but, after the installiation, the audio doesn't worked. Can i reset the audio drivers? Help me! Thanks!

---

### Post by khelben1979 on 2009-04-15
What version of Ubuntu are you using? Also, what hardware which is in that notebook might be of interest to see what possible drivers it might be using:

```
sudo lspci
```

---

### Post by MartinoM on 2009-04-15
ubuntu 8.10

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

---

### Post by MartinoM on 2009-04-15
Can someone help me?

---

### Post by khelben1979 on 2009-04-15
Have you checked the audio settings using [Alsamixer]("http://en.wikipedia.org/wiki/Alsamixer")?

---

### Post by Ciwan21 on 2009-04-15
i guys, i have installed ubuntu 8.10 couple months ago. since i haven't got any sound whatsoever.... I have read all comments, and all codes i've tried but no joy! i got really annoyed and uninstalled ubuntu then re-installed again but its still same. no sound.... im going insane :) i see so many people have fixed the issues after the instructions but why cant i do it.... please help me to get sound on ubuntu. Im nearly believe that i will never get sound :)

Any help much appreciated!

---

### Post by RuleMaker on 2009-04-15
Go to System -> Preferences -> Sound
Tell us which driver is selected in each dropdown menu.

---

### Post by Ciwan21 on 2009-04-15
ok
on Devices Tab
Sound Events --ALSA Advanced Linux Sound Architecture

Music and Movies -- ALSA Advanced Linux Sound Architecture

Audio conferencing -- 
ALSA Advanced Linux Sound Architecture
ALSA Advanced Linux Sound Architecture

Default Mixer Tracks

HDA intel (Alsa mixer)

---

### Post by RuleMaker on 2009-04-15
Ok, lets try using the ESD server.
In terminal:
```
sudo apt-get install esound
```

And then again go to the sound and select ESD in each of menus.

---

### Post by Ciwan21 on 2009-04-15
thanks, I have done that. Sound Events ESD

Music and Movies ESD
Audio Conferencing  -Sound playback ESD
Sound Capture - ALSA
Default Mixer Tracks - HDA Alsa Mixer

Right?

---

### Post by RuleMaker on 2009-04-15
Yes, that should be it, so, testing makes a sound?

---

### Post by MartinoM on 2009-04-15
i istalled the Esd but in sound i haven't the ESD Option..

---

### Post by Ciwan21 on 2009-04-15
no man, when i hit test it no sound whatsoever. I turned on youtube no sound, skype no sound. Still no sound. You seee i have win vista its working no problem. and i have virtualbox in vista and in there i have debian sound no problem :) its just ubuntu no sound and i cant understand why.....

---

### Post by RuleMaker on 2009-04-15
What's the output of:
fuser /dev/snd

---

### Post by Ciwan21 on 2009-04-15
you mean put this "fuser /dev/snd" in terminal? if so, i put it in. I got nothing, i mean it just repeat my computer user name.

---

### Post by RuleMaker on 2009-04-15
Strange...
Give this a try:
```
sudo apt-get install gstreamer0.10-esd 
```

And try to test playing a sound file from terminal with esd:

```
esdplay somefile.mp3
```

just replace somefile.mp3 with your audio file and tell us the output.

---

### Post by Ciwan21 on 2009-04-15
no joy! the output is

egsa21@ubuntu:~$ sudo apt-get install gstreamer0.10-esd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-esd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
egsa21@ubuntu:~$ esdplay Pitbull.mp3
Audio File Library: could not open file 'Pitbull.mp3' [error 3]
egsa21@ubuntu:~$

---

### Post by RuleMaker on 2009-04-15
Follow [these]("http://www.4front-tech.com/forum/viewtopic.php?t=3052&sid=acc255ff25368503cbbe8b5e77c53b99") instructions.

---

### Post by Ciwan21 on 2009-04-15
thanks for dealing with the issue. but still no joy. Can we log the issue to the Administrator or somewhere else do you know?

Thanks very much.

---

