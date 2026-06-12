---
title: "HP nc8000 - headphone problem"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by le_vainqueur on 2008-01-09
I installed Ubuntu 7.10 on my laptop, and everything worked by default except for one thing...the headphone jack.  Here's the problem: when I plug my headphones in to my laptop, I DO get audio through them, but the audio still comes through the speakers.  This is obviously problematic since I'm in libraries a lot.  

I've looked around this forum and elsewhere, but I haven't been able find anyone with a solution.

I previously had OpenSuse 10.3 on this computer and the same problem occurred.

Any tips?


Thanks,

LV

---

### Post by Lleumas on 2008-01-09
I actually have this problem as well, I found a couple threads before, but they didn't resolve my problem so I won't bother finding them. Do go to the audio preferences and make sure jack sense in enabled in the switches tab though.

---

### Post by eggdeng on 2008-01-09
This is a common problem with Intel HDA cards, among others. See if you can identify your card using ```
lspci
```The output of ```
aplay -l
```may be useful too.

---

### Post by le_vainqueur on 2008-01-09
Alright...for lspci I get:

> 00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82946GZ/PL/GL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

And for aplay -l I get:

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I'm not sure what this means.  Is there something I should be looking for?

---

### Post by napsy on 2008-01-09
ICH7 should be supported by alsa. Try to compile and install alsa manually.

---

### Post by eggdeng on 2008-01-10
Hopefully, that won't be necessary. Can you take a look at [http://ubuntuforums.org/showthread.php?t=314383]("http://ubuntuforums.org/showthread.php?t=314383")
If you need more help, post the make and model of your computer.

---

### Post by le_vainqueur on 2008-01-10
Thanks for the advice...I added the line to my list as you suggested in you post (I subbed hp for xyz), but that did not solve the problem.  When I plug my headphones in, audio still comes through built-in speakers.

My computer is an HP Compaq nc8000.  Is there anything else I can try?

---

### Post by eggdeng on 2008-01-11
Try with
```
options snd-hda-intel model=laptop-hp
```
or
```
options snd-hda-intel position_fix=1 model=3stack
```
(This one is confirmed to work with your card but the poster didn't specify his make or model.) Remember that you have to reboot for changes to take effect.

---

### Post by le_vainqueur on 2008-01-13
Thanks for the reply

I tried the two you suggested...unfortunately they don't work for me.  I also tried:

> options snd-hda-intel position_fix=1 model=hp

and

> options snd-hda-intel position_fix=1 model=laptop-hp

Neither of those did it either.  Just to make sure I'm not doing something obviously wrong, here is the file for my last itteration.

> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel position_fix=1 model=laptop-hp


Everything look the way it's supposed to?

---

### Post by eggdeng on 2008-01-14
Bummer.
Have you checked out the /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz  file? Unzip it and search for 82801G, it may give you more options.
Can you run cat /proc/asound/version. This will tell you which version of alsa you are using.
If you are using less than 1.0.15, it's probably a good idea to recompile. There are guides to this for example at [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

---

### Post by le_vainqueur on 2008-01-15
> **eggdeng said:**
> Bummer.
Have you checked out the /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz  file? Unzip it and search for 82801G, it may give you more options

I couldn't find anything for 82801G...shoot

For cat /proc/asound/version I get:

> Advanced Linux Sound Architecture Driver Version 1.0.14 (Thu May 31 09:03:25 2007 UTC)

I guess that means I need to recompile.  I'll check out those guides soon, and post the results here.

---

