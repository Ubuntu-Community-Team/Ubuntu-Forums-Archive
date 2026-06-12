---
title: "Dell XPS M1530"
date: 2008-06-21
forum: Hardware
---

### Post by tcbopper on 2008-06-21
Hello;

I have a Dell XPS M1530 Notebook.   I originally installed 7.10 and upgraded to 8.04.  It is Dual boot Vista/Ubuntu.  Everything is working as expected except for 2 things.....

1.  I have no sound in Ubuntu and in searching through the threads, it seems no one else is reporting issues w/ sound.  The movie player/Audacity/ etc. all run .... and the video is fine...just nothing comes out of the speakers.  Anyone else have to solve this issue?

2.  Many people have praised the keyboard...I find that the keyboard delivers too many keystroke....I often misspell things because "extra" letters get "in".....exaample....buuuy something, This is an issue in both Vista and Ubuntu....anyone else have this problem?

Thanks

---

### Post by argail1980 on 2008-06-21
solution to number 2 is easier:

go to the system menu > preferences > keyboard

there you can change the delay between repetition of letters (sorry, don't know the exact term, only know it in german)

problem 1:

open a terminal

Applications > Acessoires > Terminal

enter

```
lspci
```

and post the output

then enter

```
aplay -l
```

and post the output too

---

### Post by tcbopper on 2008-06-21
Thanks.....

BTW....I've tried the keyboard suggestion already(and in the Vista control panel) to no avail.....I do realize that the OS's are completely independent.....

Here's the output:


ken@ken-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
ken@ken-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ken@ken-laptop:~$

---

### Post by tcbopper on 2008-06-21
Update.....the sound does work....just that the hardware button needs to be at maximum volume, Ubuntu needs to be set at maximum volume and the application must be set to maximum volume....and then it is very soft/quiet (barely audible).....

Any way to boost the output?

---

### Post by tcbopper on 2008-06-21
Update 2....

Audacity now gives this error message

Error while opening sound device. Please check the output device settings and the project sample rate.

---

### Post by argail1980 on 2008-06-21
open an editor with as root:

hit Alt+F2 and enter ```
gksudo gedit /etc/modprobe.d/alsa-base
```
and add a line there 


```
options snd-hda-intel model=3stack
```
and restart the sound system (or the computer)

If that does not work, play around with those models....

the available models for hda-intel cards are listed in the file

```
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
```

there are some dell modules, but which one to use, you'll just have to try out. replace the '3stack' with the appropriate model name then

---

