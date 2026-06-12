---
title: "Internal speakers do not mute when using headphones"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by gogodidi on 2007-08-26
Hello, I got a brand new HP dv9510(eo) model laptop two days ago, and since then I have managed to get most things to work. The biggest problem is one I have been struggling with for a few hours now (last night and this morning): the internal speakers will not mute when a headphone is plugged in.

The headphone will get the sound also, but the speakers continue to play. This kind of defeats the purpose of the headphones.

I have tried the information found at this page and have compiled the latest version of alsa with the patch, and it still does not work. I have also been googling for any pages that might, help and have not found anything among the billions of useless "lulz plz hlp m" pages.

I know that many people have this problem, but with them it is often a simple "check that in volume control" solution or "your hardware is busted". 

My problem is similar to those seen in theseubuntuforum threads, all unsolved:
[http://ubuntuforums.org/showthread.php?t=500894](http://ubuntuforums.org/showthread.php?t=500894)
[http://ubuntuforums.org/showthread.php?t=446782](http://ubuntuforums.org/showthread.php?t=446782)

Some data:

Feisty Fawn.

$ uname -a
```
Linux Thies 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux
```

$ lspci
```
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

I really hope I can get this figured out. I would be most grateful for any help whatsoever.

Thanks.

---

### Post by gogodidi on 2007-08-30
well, Im glad this worked out well for me...

---

### Post by lawr_rawr on 2007-08-30
I have a similar Nvidia audio device (nVidia Corporation MCP51 High Definition Audio (rev a2)), and I have to manually mute "front" to disable the speakers. Maybe you have already tried this, but read my posts in this thread:
[http://ubuntuforums.org/showthread.php?t=442841](http://ubuntuforums.org/showthread.php?t=442841)

There is no "headphone jack sense" option for my audio device... so the only way I could do it was to manually enable/disable the speakers.

---

### Post by lien_meat on 2007-09-04
I have some news!  I have a Compaq v3015nr, which has the same audio chipset as does lawr_rawr.  I have gotten headphone sense working!

Here's the important info:
distro: Ubuntu 7.04 Feisty Fawn
kernel: 2.6.20-16-generic (just the regular one from ubuntu, not custom or anything)
alsa: 
alsa-base_1.0.13-3ubuntu1_all.deb
alsa-firmware-loaders
alsa-oss

The magic though is this line I added in /etc/modprobe.d/alsa-base:
```

options snd-hda-intel model=laptop

```
(in the past to get any sound to work I had to install alsa from source, but it seems feisty has fixed this. I can't confirm whether adding this line to a "from-source" install of alsa works, but I would suppose so.)

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
#options snd-cmipci mpu_port=0x330 fm_port=0x388

####### These are ones I've tried recently! (none work...) ############
#options snd-hda-intel model=ref
#options snd-hda-intel model=laptop-hp
#options snd-hda-intel model=m2-2
#options snd-hda-intel index=0 disable_msi=1
#options snd-hda-intel model=z71v position_fix=1

####### This one works! ##########
options snd-hda-intel model=laptop

```

I've tried loads of other models/options trying to get something working. Nothing has come close to working as well as this does for me.  It auto-mutes the speakers just like it should when you plug in headphones just like it's supposed to now, and unmutes when you take them out.  Previously I had it working so that I could use the mute button as a toggle, but for some reason that stopped working all of the sudden one day.  I backed up all my config files and alsa related .debs just in case something breaks (again).  Hopefully this will help you.  I know MOST HP laptops use exactly the same chipset as mine, and I happen to have a bios from HP on my machine...so chances are this fix will work for you too.
-Eric

---

### Post by lawr_rawr on 2007-09-07
Sadly, your fix doesn't work for me. Maybe there's something different hardware-wise between our laptops. :-(

---

### Post by joerite on 2007-12-17
worked for me

---

### Post by kvonb on 2008-01-09
-

---

### Post by Gavigan280 on 2008-02-11
Having the same problem as OP; same hardware as well, running an HP Pavillion DV6000:


```
~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```
```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Tried the "options snd-hda-intel model=laptop" fix and "options snd-hda-intel model=laptop-hp" as well.  Also updated alsa to 1.0.16 to no avail.  Some help with this would be really nice.

---

### Post by beatryder on 2008-02-11
> **lien_meat said:**
> 
The magic though is this line I added in /etc/modprobe.d/alsa-base:
```

options snd-hda-intel model=laptop

```
(in the past to get any sound to work I had to install alsa from source, but it seems feisty has fixed this. I can't confirm whether adding this line to a "from-source" install of alsa works, but I would suppose so.)

```

####### This one works! ##########
options snd-hda-intel model=laptop

```


I have a Dell Latitude D620 and this worked for me.

---

### Post by oldsoundguy on 2008-02-11
Seems a shame to have to do all that for something that is USUALLY mechanical.  In MOST cases the speaker lead goes THROUGH the headphone jack and when you insert the jack it physically interrupts the feed to the speakers.  Only on "headphone monitoring" jacks on pro audio equipment is this not done.  Shame the manufacturers have moved away from a very simple solution.

---

### Post by flightless bird on 2008-04-06
> **joerite said:**
> worked for me

And me! :)

---

### Post by monkeymind90 on 2008-04-13
I have a HP dv6700. This fix does not work for me, and I've tried all the stuff in the links provided. I'm pretty new to Ubuntu. I'm running the generic Gutsy (64bit). Any ideas?

---

### Post by Eraser on 2008-04-14
This was a "no go" for me as well. I have an HP Pavilion dv6810us.

I'm on Gutsy 64bit. Tried compiling Alsa form source, didn't work either :(

---

### Post by Scorpion1031 on 2008-04-14
I had the same problem with my Realtek device.  I tried a ton of different options and then I found this thread:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

I tried a few of the configurations and it finally worked.  Give it a try.

---

### Post by monkeymind90 on 2008-04-14
> **Scorpion1031 said:**
> I had the same problem with my Realtek device.  I tried a ton of different options and then I found this thread:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

I tried a few of the configurations and it finally worked.  Give it a try.

I tried what he advised, but my ID is Conexant 5051, which is not on the list. Any ideas?
Thanks

---

### Post by lych on 2008-04-26
Hello Guys!!

I think I have figured out how to fix this non-muting internal speakers, at least it worked out for me.

Yes, like it worked out for somebody, the general idea is to add ```
options snd-hda-intel model=xxx
``` into /etc/modprobe.d/alsa-base.

Value "model=laptop" as suggested by someone before does not work for everybody and did not work for me also.

But searching over I found the following in alsa-kernel/Documentation/ALSA-Configuration.txt:
```
Model name    Description
          ----------    -----------
        ALC880
          3stack        3-jack in back and a headphone out
          3stack-digout 3-jack in back, a HP out and a SPDIF out
          5stack        5-jack in back, 2-jack in front
          5stack-digout 5-jack in back, 2-jack in front, a SPDIF out
          6stack        6-jack in back, 2-jack in front
          6stack-digout 6-jack with a SPDIF out
          w810          3-jack
          z71v          3-jack (HP shared SPDIF)
          asus          3-jack (ASUS Mobo)
          asus-w1v      ASUS W1V
          asus-dig      ASUS with SPDIF out
          asus-dig2     ASUS with SPDIF out (using GPIO2)
          uniwill       3-jack
          F1734         2-jack
          lg            LG laptop (m1 express dual)
          lg-lw         LG LW20/LW25 laptop
          tcl           TCL S700
          clevo         Clevo laptops (m520G, m665n)
          test          for testing/debugging purpose, almost all controls can be
                        adjusted.  Appearing only when compiled with
                        $CONFIG_SND_DEBUG=y
          auto          auto-config reading BIOS (default)
```

My laptop is LG LW40, so I just put this  into my /etc/modprobe.d/alsa-base:
```
options snd-hda-intel model=lg-lw
```

Then reloaded "snd_hda_intel" kernel module:
```
# rmmod snd_hda_intel
# modprobe snd_hda_intel
```

And now my internal speakers do mute when plugging an external sound jack!!

Oh.. Thanks everybody and good luck!

---

