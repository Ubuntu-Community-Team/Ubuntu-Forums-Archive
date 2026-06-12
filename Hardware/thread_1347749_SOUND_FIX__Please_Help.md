---
title: "SOUND FIX:  Please Help"
date: 2009-12-06
forum: Hardware
---

### Post by brhokla on 2009-12-06
Trying to get my Sound to work on a HP DV4-2045dx AMD 64x2 laptop.  Another poster said they added.
 

 # Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1  
 

 to:     etc/modprobe.d/alsa-base.conf  
 

 I however can't get this to save to the file so I can reboot and test it.   
 

 Here is the file I'm trying to add it too......
 

 

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
 install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; } 
 # 
 # Workaround at bug #499695 (reverted in Ubuntu see LP #319505) 
 install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; } 
 install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; } 
 install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; } 
 # 
 install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; } 
 # Cause optional modules to be loaded above sound card driver modules 
 install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; } 
 install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; } 
  
 # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway) 
 install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; } 
 # Prevent abnormal drivers from grabbing index 0 
 options bt87x index=-2 
 options cx88_alsa index=-2 
 options saa7134-alsa index=-2 
 options snd-atiixp-modem index=-2 
 options snd-intel8x0m index=-2 
 options snd-via82xx-modem index=-2 
 options snd-usb-audio index=-2 
 options snd-usb-us122l index=-2 
 options snd-usb-usx2y index=-2 
 options snd-usb-caiaq index=-2 
 # Ubuntu #62691, enable MPU for snd-cmipci 
 options snd-cmipci mpu_port=0x330 fm_port=0x388 
 # Keep snd-pcsp from being loaded as first soundcard 
 options snd-pcsp index=-2 
 # Power down HDA controllers after 10 idle seconds 
 options snd-hda-intel power_save=10 power_save_controller=N
 

 

 I'm trying to add :   
 

 

 # Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1 
options snd-hda-intel enable_msi=1  
 

 Computer won't let me save claiming it's read only and that I have no permissions.  Any ideas?  Poster stated this fixed his sound.  I need to fix mine before toss this computer in the trash.

---

### Post by gordintoronto on 2009-12-06
From a terminal session, type (or cut-and-paste):

gksudo gedit /etc/modprobe.d/alsa-base.conf

That should give you permission to save the file.

---

### Post by lidex on 2009-12-06
Have a look here:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

The alsa upgrade fixed my DV7 audio problem but that was on Jaunty. You did not specify but I assume it will work for karmic also.

---

