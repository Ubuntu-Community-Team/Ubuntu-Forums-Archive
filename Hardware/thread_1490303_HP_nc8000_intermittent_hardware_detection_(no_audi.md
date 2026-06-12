---
title: "HP nc8000 intermittent hardware detection (no audio, shutdown, usb, random"
date: 2010-05-22
forum: Hardware
---

### Post by bbking67 on 2010-05-22
Okay so I am new to Linux.  Be kind.  I have installed Ubuntu 10.04 LTS on my old HP nc8000 and with some forum help got my 3G USB stick working.

But... every reboot is a new adventure:

- some sessions I cannot shut down.  Pressing shut down in the menu brings me to the login screen.  Same for the hardware power button.  I end up having to hold the power button 5 seconds or so to force a power off

- some sessions I get no audio.  Nothing listed under prefs-sound-hardware.  Other sessions it works fine.

- Some sessions my USB mobile broadband gives me an "unable tro mount mobile connect, not authorized" message

Other times everything works, or only one or two of the problems are happening.

I have a feeling some of these are related... any suggestions?  And going back to Windows isn't going to happen anytime soon.:confused:

---

### Post by Joe of loath on 2010-05-22
Boot from the CD and select 'check memory', as well as 'check disk for defects'. Sounds like when one of my boxes had a dodgy RAM module.

---

### Post by bbking67 on 2010-05-23
It's very unlikely to be a hardware problem.  System worked perfectly with XP up until upgrade to Ubuntu.  I'll scan it anyway.

Most sessions are messing up on shutdown and have no sound.

/bb

---

### Post by bbking67 on 2010-05-26
well i guess its back to winblows then...

---

### Post by Joe of loath on 2010-05-27
what's the output of lspci when stuff works, and the output when it doesn't?

---

### Post by bbking67 on 2010-05-29
Okay when everything is working properly (audio, 3G wireless, shutdown) I get the following output from lspci:
 
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
 
```
 
 
But when it is not working I get the following:
 
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
```
 
Pretty much looks the same, but when it is not working there is nothing listed under system-preferennces-sound-hardware, but when it's working it lists the device as "internal audio".
 
/bbking67

---

### Post by lidex on 2010-05-31
Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

Now can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by bbking67 on 2010-05-31
Might take me a while.  I completely screwed up my drive and now I can't even get windows back on it.  I was trying to dual-boot... if I install windows I get a disk error (even tried fdisk /mbr to no avail) and I get a weird grep console if i install ubuntu.

so i am going to try a factory low-level on the hd and then try again, either that or get the drive changed under warranty (it's brand new).

believe it or not i'm an IT guy... I can't believe how much has gone wrong!

//bbking67

---

### Post by auser2010 on 2010-06-04
Hi!
I'm experiencing the very same problem here. My hardware includes an M4A79XTD EVO mobo with an AMD Phenom II X4 955 CPU and an "Point of View G210" graphics card (nVidia based).
When the problem appears, all the symptoms are simultaneously present: no sound, no shutdown and also no CPU frequency policy working  (frequency always stuck to the max and fans spinning fast).

I noticed the wrong behaviour very often when the nVidia proprietary drivers were installed (from the official repository). Then I switched back to the "nouveau" drivers and the problem seemed mitigated, but actually it pops up again when I boot the system with a WiFi dongle connected.:confused:

I'm able to shutdown the system only by typing in a terminal:
```
sudo poweroff
```I add the information requested by lidex to bbking67: when the system starts correctly I have the following
```
ubuntu2010@lucid-desktop:~$ uname -a
Linux lucid-desktop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
ubuntu2010@lucid-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ubuntu2010@lucid-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
ubuntu2010@lucid-desktop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: VIA VT1708S

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID b

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID b
ubuntu2010@lucid-desktop:~$ 

```When it starts in "bad mode" the only difference is that the "aplay" command gives:
```

aplay: device_list:223: no soundcards found...

```This is the output of lspci:
```

00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403

```On a second HDD I have a Kubuntu 8.04 with the latest nVidia drivers obtained from the nVidia site, and the latest alsa package compiled from source and it runs fine all the times. :)

auser2010

---

### Post by auser2010 on 2010-06-05
It seems that this (or similar) problem has got many hits:

[https://bugs.launchpad.net/ubuntu/+bug/576235](https://bugs.launchpad.net/ubuntu/+bug/576235)

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/584337](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/584337)

[http://ubuntuforums.org/showthread.php?t=1472269](http://ubuntuforums.org/showthread.php?t=1472269)

and probably more.

It looks like a fat furry bug... :-k


auser2010

---

### Post by bbking67 on 2010-06-06
Okay I finally got Linux booting again.  I can't get dual-boot with XP working... ended up fixing my problems using Acronis (long story).  Anyway, I have Ubuntu 10.04 installed and it still exhibits the same weird problems.

Here is the output as requested:

```
chris@nc8000-linux:~$ uname -a
Linux nc8000-linux 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

chris@nc8000-linux:~$ aplay -l
aplay: device_list:223: no soundcards found...

chris@nc8000-linux:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

chris@nc8000-linux:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory
```

..looking for suggestions... actually i am thinking of going to an older ubuntu.  if this is a bug, would that help?

---

### Post by lidex on 2010-06-06
I think this may be a bug. What is this output:
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```
What does windows detect your audio driver as?

---

### Post by bbking67 on 2010-06-06
```
chris@nc8000-linux:~$ head -1 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Analog Devices AD1981B
```

/bbking67

---

### Post by lidex on 2010-06-06
Hmm. OK, how about this:
```
lsmod | grep snd
```

---

### Post by bbking67 on 2010-06-06
```
chris@nc8000-linux:~$ lsmod | grep snd
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
```

---

### Post by lidex on 2010-06-06
This is somewhat confusing - at least for me. I'll need you to do a couple of things. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.

Next use the alsa-upgrade link in my sig to get v 1.0.23

Finally: Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by bbking67 on 2010-06-06
[http://www.alsa-project.org/db/?f=92360ce4254f0436590323c8e594ffdc5c38398a](http://www.alsa-project.org/db/?f=92360ce4254f0436590323c8e594ffdc5c38398a)

---

### Post by lidex on 2010-06-06
The kernel is right, but not alsa. Did you run the upgrade script? You'll need to uninstall alsa-backports first.

---

### Post by bbking67 on 2010-06-06
i ran the two scripts but I was already up to date...

???

/bbking67

---

### Post by lidex on 2010-06-06
> **bbking67 said:**
> i ran the two scripts but I was already up to date...

???

/bbking67
How do you figure?
From your alsa-info:
> !ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22



---

### Post by bbking67 on 2010-06-06
sorry you mean alsa is out of date!  I will do it as soon as I get the chance... sorry.

---

### Post by bbking67 on 2010-06-07
Okay so the also site appears to be down at the moment... the script runs, but can't download the latest drivers, firmware, etc. I tried downloading manually via the also website and the files are coming at 0 bytes. The mirrors seem to be out of date, so I guess I am snookered for tonight. Hopefully the site is back soon.
 
Okay I guess the main mirror is down... there was one mirror with all the files and I downloaded everything (I think). Now what can I do with them?  I have no idea how to compile, etc.

---

### Post by bbking67 on 2010-06-10
is there any other way to do this without the ftp access to alsa website?  It is still not working.

---

