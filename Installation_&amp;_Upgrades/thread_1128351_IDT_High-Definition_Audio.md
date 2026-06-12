---
title: "IDT High-Definition Audio"
date: 2009-04-17
forum: Installation &amp; Upgrades
---

### Post by optimistique1 on 2009-04-17
Hi All

I finally managed to install 9.04 onto my brand new HP DV2-1010 notebook.
However, this time I have no sound :-(
I have checked all the obvious places and played about with the volume controls/preferences  with no luck...
The Audio drivers for Windows Vista are IDT High-Definition Audio CODEC Driver.  Is there a way to find something similar for Ubuntu?
Many thanks
Garry

My specs are:

AMD Athlon Neo Processor MV40 (1.60GHz, 512KB cache) 

ATI Radeon HD3410 Graphics Card

---

### Post by optimistique1 on 2009-04-17
.

---

### Post by camac014 on 2009-04-23
I also am dual-booting Ubuntu and Win 7 on a Gateway FX-6831.

Sound works great on Windows, but only through headphones in Ubuntu.

Help would be greatly appreciated (I had this problem before but this is a fresh install and I forgot how I had fixed it...)

---

### Post by ic3000 on 2009-04-25
Hi optimistique1,

Please to know that someone was able to install 9.04 on DV2...

Could you please post the trick here? Im trying to made the same with no sucsses!

I saw that someone have post a bug report on lauchpad with this problem and maybe this thread could help!

[https://bugs.launchpad.net/ubuntu/+bug/366678](https://bugs.launchpad.net/ubuntu/+bug/366678)

Thanks!

---

### Post by optimistique1 on 2009-04-26
Hi Buddy, if you install with the alterative install CD that works perfectly and installs without problems.  However, sa you guessed by my post there is no sound.  I have tried several suggested solutions and none have worked.

I have tried the following with no luck at all - 

1. copy-paste the following command into the Terminal:
gksudo gedit /etc/modprobe.d/alsa-base
2. and add this line to the end of the file:
options snd-hda-intel enable_msi=1
3. Then navigate to System>Preferences>Sound and change everything to ALSA
4. reboot and retest sound
AND

1. copy-paste the following command into the Terminal:
gksudo gedit /etc/modprobe.d/alsa-base
2. and add these lines to the end of the file:
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1
3. Then navigate to System>Preferences>Sound and change everything to ALSA
4. reboot and retest sound


I tried both options and none of them worked I am still without any sound. I used the System Testing thing in Administration and here is what it says about my sound - 

/etc/modprobe.d/alsa-base.conf

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
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2


Back to Table of Contents
/etc/modprobe.d/blacklist-watchdog.conf

# Watchdog drivers should not be loaded automatically, but only if a
# watchdog daemon is installed.
blacklist acquirewdt
blacklist advantechwdt
blacklist alim1535_wdt
blacklist alim7101_wdt
blacklist booke_wdt
blacklist cpu5wdt
blacklist eurotechwdt
blacklist i6300esb
blacklist i8xx_tco
blacklist ib700wdt
blacklist ibmasr
blacklist indydog
blacklist ixp2000_wdt
blacklist ixp4xx_wdt
blacklist machzwd
blacklist mixcomwd
blacklist mpc8xx_wdt
blacklist mpcore_wdt
blacklist mv64x60_wdt
blacklist pcwd
blacklist pcwd_pci
blacklist pcwd_usb
blacklist s3c2410_wdt
blacklist sa1100_wdt
blacklist sbc60xxwdt
blacklist sb8360
blacklist sc1200wdt
blacklist sc520_wdt
blacklist scx200_wdt
blacklist shwdt
blacklist softdog
blacklist w83627hf_wdt
blacklist w83877f_wdt
blacklist w83977f_wdt
blacklist wafer5823wdt
blacklist wdt
blacklist wdt_pci


Back to Table of Contents
/etc/modprobe.d/blacklist-framebuffer.conf

# Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem. For this reason we
# never load them automatically.
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist cyblafb
blacklist gx1fb
blacklist hgafb
blacklist i810fb
blacklist intelfb
blacklist kyrofb
blacklist lxfb
blacklist matroxfb_base
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist rivafb
blacklist s1d13xxxfb
blacklist savagefb
blacklist sisfb
blacklist sstfb
blacklist tdfxfb
blacklist tridentfb
blacklist vesafb
blacklist vfb
blacklist vga16fb
blacklist vt8623fb


Back to Table of Contents
/etc/modprobe.d/alsa-base

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1




Back to Table of Contents
/etc/modprobe.d/blacklist-modem.conf

# Uncomment these entries in order to blacklist unwanted modem drivers
# blacklist snd-atiixp-modem
# blacklist snd-intel8x0m
# blacklist snd-via82xx-modem


Back to Table of Contents
/etc/modprobe.d/blacklist-oss.conf

blacklist ac97
blacklist ac97_codec
blacklist ac97_plugin_ad1980
blacklist ad1848
blacklist ad1889
blacklist adlib_card
blacklist aedsp16
blacklist ali5455
blacklist btaudio
blacklist cmpci
blacklist cs4232
blacklist cs4281
blacklist cs461x
blacklist cs46xx
blacklist emu10k1
blacklist es1370
blacklist es1371
blacklist esssolo1
blacklist forte
blacklist gus
blacklist i810_audio
blacklist kahlua
blacklist mad16
blacklist maestro
blacklist maestro3
blacklist maui
blacklist mpu401
blacklist nm256_audio
blacklist opl3
blacklist opl3sa
blacklist opl3sa2
blacklist pas2
blacklist pss
blacklist rme96xx
blacklist sb
blacklist sb_lib
blacklist sgalaxy
blacklist sonicvibes
blacklist sound
blacklist sscape
blacklist trident
blacklist trix
blacklist uart401
blacklist uart6850
blacklist via82cxxx_audio
blacklist v_midi
blacklist wavefront
blacklist ymfpci
blacklist ac97_plugin_wm97xx
blacklist ad1816
blacklist audio
blacklist awe_wave
blacklist dmasound_core
blacklist dmasound_pmac
blacklist harmony
blacklist sequencer
blacklist soundcard
blacklist usb-midi


Back to Table of Contents
/etc/modprobe.d/blacklist-ath_pci.conf

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath_pci



Back to Table of Contents
/etc/modprobe.d/blacklist.conf

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


Back to Table of Contents
/etc/modprobe.d/alsa-base~

# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1




Back to Table of Contents
/etc/modprobe.d/libpisock9.conf

blacklist visor


Back to Table of Contents
/etc/modprobe.d/blacklist-firewire.conf

# Select the legacy firewire stack over the new CONFIG_FIREWIRE one.

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2


Back to Table of Contents
/etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp



ALSA Timer Device
Property Value
info.category alsa
info.subsystem sound
info.product ALSA Timer Device
info.parent /org/freedesktop/Hal/devices/computer
info.capabilities alsa access_control
info.udi /org/freedesktop/Hal/devices/computer_alsa_timer
info.callouts.add hal-acl-tool --add-device
info.callouts.remove hal-acl-tool --remove-device
linux.device_file /dev/snd/timer
linux.hotplug_type 2
linux.subsystem sound
linux.sysfs_path /sys/devices/virtual/sound/timer
access_control.type sound
access_control.file /dev/snd/timer
alsa.device_file /dev/snd/timer
alsa.type timer 


OSS Sequencer Device
Property Value
info.category oss
info.subsystem sound
info.product OSS Sequencer Device
info.parent /org/freedesktop/Hal/devices/computer
info.capabilities oss access_control
info.udi /org/freedesktop/Hal/devices/computer_oss_sequencer_0
info.callouts.add hal-acl-tool --add-device
info.callouts.remove hal-acl-tool --remove-device
oss.device_file /dev/sequencer2
oss.type sequencer
access_control.type sound
access_control.file /dev/sequencer2
linux.device_file /dev/sequencer2
linux.hotplug_type 2
linux.subsystem sound
linux.sysfs_path /sys/devices/virtual/sound/sequencer2
OSS Sequencer Device
Property Value
info.category oss
info.subsystem sound
info.product OSS Sequencer Device
info.parent /org/freedesktop/Hal/devices/computer
info.capabilities oss access_control
info.udi /org/freedesktop/Hal/devices/computer_oss_sequencer
info.callouts.add hal-acl-tool --add-device
info.callouts.remove hal-acl-tool --remove-device
oss.device_file /dev/sequencer
oss.type sequencer
access_control.type sound
access_control.file /dev/sequencer
linux.device_file /dev/sequencer
linux.hotplug_type 2
linux.subsystem sound
linux.sysfs_path /sys/devices/virtual/sound/sequencer
ALSA Sequencer Device
Property Value
info.category alsa
info.subsystem sound
info.product ALSA Sequencer Device
info.parent /org/freedesktop/Hal/devices/computer
info.capabilities alsa access_control
info.udi /org/freedesktop/Hal/devices/computer_alsa_sequencer
info.callouts.add hal-acl-tool --add-device
info.callouts.remove hal-acl-tool --remove-device
linux.device_file /dev/snd/seq
linux.hotplug_type 2
linux.subsystem sound
linux.sysfs_path /sys/devices/virtual/sound/seq
access_control.type sound
access_control.file /dev/snd/seq
alsa.device_file /dev/snd/seq
alsa.type sequencer


Hope someone can help or else I will have to go back to the dreaded Windowz  ((

---

### Post by skeets011 on 2009-07-02
I think there has to be some switch (which I have yet to find) to select which device to output to speakers, headphones, or the hdmi port.  I have not successfully heard any sound from the speakers but have audio through the headphone jack by default.  I have yet to try the hdmi port.

---

### Post by mr_raider on 2009-07-04
I got my sound working on a dv2-1043ca using this technique:

[http://ubuntuforums.org/showthread.php?t=1073090](http://ubuntuforums.org/showthread.php?t=1073090)


Interestingly, sound works fine on Intrepid, and if you have the integrated ATI x1250 IGP, you may be better served with Intrepid.

---

