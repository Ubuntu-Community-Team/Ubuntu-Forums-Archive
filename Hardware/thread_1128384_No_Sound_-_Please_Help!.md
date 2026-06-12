---
title: "No Sound - Please Help!"
date: 2009-04-17
forum: Hardware
---

### Post by optimistique1 on 2009-04-17
Help - No Sound!!!! 

--------------------------------------------------------------------------------

Hi All

I finally managed to install 9.04 onto my brand new HP DV2-1010 notebook.
However, this time I have no sound 
I have checked all the obvious places and played about with the volume controls/preferences with no luck...
The Audio drivers for Windows Vista are IDT High-Definition Audio CODEC Driver. Is there a way to find something similar for Ubuntu?
Many thanks
Garry

My specs are:

AMD Athlon Neo Processor MV40 (1.60GHz, 512KB cache) 

ATI Radeon HD3410 Graphics Card

PS: I posted in the wrong forum originally but no sure how to delete a post...;)

---

### Post by hotweiss on 2009-04-17
> **optimistique1 said:**
> Help - No Sound!!!! 

--------------------------------------------------------------------------------

Hi All

I finally managed to install 9.04 onto my brand new HP DV2-1010 notebook.
However, this time I have no sound 
I have checked all the obvious places and played about with the volume controls/preferences with no luck...
The Audio drivers for Windows Vista are IDT High-Definition Audio CODEC Driver. Is there a way to find something similar for Ubuntu?
Many thanks
Garry

My specs are:

AMD Athlon Neo Processor MV40 (1.60GHz, 512KB cache) 

ATI Radeon HD3410 Graphics Card

PS: I posted in the wrong forum originally but no sure how to delete a post...;)

Open a terminal window, and type "aplay -l". This will tell you what sound card you have, and then we can move on from there...

This works on some HP laptops:

1) Double click on the speaker icon in the System Tray to bring up the mixer.

2) Go into preferences and make sure that "External Amplifier" is selected to show on the mixer.

3) When you go back to the mixer, you will have a new tab "Switches." Select that tab.

4) Uncheck the only box on that tab. It's the box marked external amplifier.

5) Close mixer.

---

### Post by optimistique1 on 2009-04-22
Hi, here are the hardware results - 

garry@GARRY:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
garry@GARRY:~$


Tried your instructions but still no sound :(:(:(
Hope you can help me out.

---

### Post by hotweiss on 2009-04-22
Try this:

[http://ubuntuforums.org/showpost.php?p=6194461&postcount=3](http://ubuntuforums.org/showpost.php?p=6194461&postcount=3)

And if that doesn't work try this (undo previous steps first):

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/63526](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/63526)

---

### Post by optimistique1 on 2009-04-22
Many thanks for your help hotweiss.
Will give this a try when I get home from work:)
Fingers crossed it works..

---

### Post by optimistique1 on 2009-04-25
Hi, I tried both options and none of them worked I am still without any sound.  I used the System Testing thing in Administration and here is what it says about my sound - 

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
# suspend failures, kernel panics and general mayhem.  For this reason we
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
Property	Value
info.category	alsa
info.subsystem	sound
info.product	ALSA Timer Device
info.parent	/org/freedesktop/Hal/devices/computer
info.capabilities	alsa access_control
info.udi	/org/freedesktop/Hal/devices/computer_alsa_timer
info.callouts.add	hal-acl-tool --add-device
info.callouts.remove	hal-acl-tool --remove-device
linux.device_file	/dev/snd/timer
linux.hotplug_type	2
linux.subsystem	sound
linux.sysfs_path	/sys/devices/virtual/sound/timer
access_control.type	sound
access_control.file	/dev/snd/timer
alsa.device_file	/dev/snd/timer
alsa.type	timer 


OSS Sequencer Device
Property	Value
info.category	oss
info.subsystem	sound
info.product	OSS Sequencer Device
info.parent	/org/freedesktop/Hal/devices/computer
info.capabilities	oss access_control
info.udi	/org/freedesktop/Hal/devices/computer_oss_sequencer_0
info.callouts.add	hal-acl-tool --add-device
info.callouts.remove	hal-acl-tool --remove-device
oss.device_file	/dev/sequencer2
oss.type	sequencer
access_control.type	sound
access_control.file	/dev/sequencer2
linux.device_file	/dev/sequencer2
linux.hotplug_type	2
linux.subsystem	sound
linux.sysfs_path	/sys/devices/virtual/sound/sequencer2
OSS Sequencer Device
Property	Value
info.category	oss
info.subsystem	sound
info.product	OSS Sequencer Device
info.parent	/org/freedesktop/Hal/devices/computer
info.capabilities	oss access_control
info.udi	/org/freedesktop/Hal/devices/computer_oss_sequencer
info.callouts.add	hal-acl-tool --add-device
info.callouts.remove	hal-acl-tool --remove-device
oss.device_file	/dev/sequencer
oss.type	sequencer
access_control.type	sound
access_control.file	/dev/sequencer
linux.device_file	/dev/sequencer
linux.hotplug_type	2
linux.subsystem	sound
linux.sysfs_path	/sys/devices/virtual/sound/sequencer
ALSA Sequencer Device
Property	Value
info.category	alsa
info.subsystem	sound
info.product	ALSA Sequencer Device
info.parent	/org/freedesktop/Hal/devices/computer
info.capabilities	alsa access_control
info.udi	/org/freedesktop/Hal/devices/computer_alsa_sequencer
info.callouts.add	hal-acl-tool --add-device
info.callouts.remove	hal-acl-tool --remove-device
linux.device_file	/dev/snd/seq
linux.hotplug_type	2
linux.subsystem	sound
linux.sysfs_path	/sys/devices/virtual/sound/seq
access_control.type	sound
access_control.file	/dev/snd/seq
alsa.device_file	/dev/snd/seq
alsa.type	sequencer


Hope someone can help or else I will have to go back to the dreaded Windowz :-(((

---

### Post by iainfarrell on 2009-05-13
Just adding to this thread that I am having the same issue at the moment with a DV2 1020. If anyone can shed any light on this it would be fab!

---

### Post by shadowlemon on 2009-05-13
try installing the gnome soundmixer, it solved many problems for me

---

### Post by asujosh1 on 2009-05-13
I also have the 1020 and nothing so far has worked.  I tried all of the instructions on this list, including installing the sound mixer, but nothing has worked.  

Any help is greatly appreciated!

BTW, total noob, first install of Ubuntu...

---

### Post by optimistique1 on 2009-06-02
I just got a reply from the bug I reported to Launchpad and it tells me to downloads the following file and install.
The file is: 
alsa-driver-snapshot.tar.gz, 

The install instructions are:

#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot

Can someone in plain simple terms tell me how to install file as I have not got a clue?

Many thanks

Garry

---

### Post by JesseDegenerate on 2009-06-02
sadly i had a similar problem with my HP Mini 1000. 

I honestly wanted Ubuntu to be that Netbook's platform of choice, but after trying 2 kernels, updating to 2.1.9 of the audio drivers, having no luck with any updates from any of the non stable repositories. (sorry i'm a linux nub)

When i updated the kernel, i got audio, but the wifi broke. 

What's even worse? I was able to get OS X (10.5.6) to install on this netbook, with full video acceleration, audio, wifi in about 6 hours. 

what could possibly be worse than that? 
It feels faster than the 9.04 netbook remix i had on it.

---

### Post by shinjimx on 2009-07-25
> **optimistique1 said:**
> I just got a reply from the bug I reported to Launchpad and it tells me to downloads the following file and install.
The file is: 
alsa-driver-snapshot.tar.gz, 

The install instructions are:

#> ./configure --enable-dynamic-minors
#> make
#> sudo make install-modules
#> sudo vim /etc/modprobe.d/alsa-base
[add 'options snd_hda_intel model=hp-dv5' sans quotes to the bottom of the file, even if you have a dv4, etc.]
#> sudo reboot

Can someone in plain simple terms tell me how to install file as I have not got a clue?

Many thanks

Garry

I've just did this on my dv2-1020la (Latinamerican version), worked like a charm.

What you have to do in simple steps:

go to this website:

[http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/)

Download the file alsa-driver-snapshot.tar.bz2

Go to your download location, extract it (I did it via the file manager, double click the file and drag 'n drop the folder to where you want, say, Desktop)

Open a terminal (command line)

Go to the location you extracted the alsa-driver folder (if you did it on Desktop, type cd /home/xxx/Desktop/alsa-driver/ where xxx is your user)

Type the commands one after the other ends:
./configure --enable-dynamic-minors
make
sudo make install-modules
sudo gedit /etc/modprobe.d/alsa-base (I replaced vim with gedit because it's easier)

copy and paste this:
options snd_hda_intel model=hp-dv5

save the file and restart your laptop

As I said, just did it (took me about 10-15 min.) and now Metallica is rocking on my system.

Good luck.
Greetings from Mexico City

---

### Post by MasterOfTheHat on 2009-07-26
For an HP dv4-1435dx, had to add following line to /etc/modprobe.d/alsa-base.conf:
```
options snd_hda_intel model=hp enable-msi=1
```

And then just restart alsa:
```
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```

Found a lot of information in [this thread]("http://ubuntuforums.org/showthread.php?t=1043568").

---

### Post by MasterOfTheHat on 2009-09-13
For what it's worth, I was still having some issues with the volume and volume control and also with the sound after coming back from hibernating.

Tonight I upgraded Alsa to 1.0.21 from the default 1.0.18rc3 that comes with Jaunty. I also tweaked the alsa-config line in the previous post from "model=hp" to "model=hp-dv5". Removing "enable-msi=1" took sound away completely. 

So far, the volume issues seem to be resolved. I'll have to wait and see if the hibernation issue goes away...

[Link to the Alsa upgrade instructions]("http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/").
[Link to HD Audio model options]("http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt").

Line added to /etc/modprobe.d/alsa-base.conf:
```
options snd_hda_intel model=hp enable-msi=1
```

Hardware devices:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Alsa version:
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Sep 12 2009 for kernel 2.6.28-15-generic (SMP).
```

Restart alsa without bouncing box:
```
killall pulseaudio
sudo alsa force-reload
pulseaudio -D
```

---

### Post by karlakoala on 2009-09-16
> **shinjimx said:**
> I've just did this on my dv2-1020la (Latinamerican version), worked like a charm.

What you have to do in simple steps:

go to this website:

[http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/)

Download the file alsa-driver-snapshot.tar.bz2

Go to your download location, extract it (I did it via the file manager, double click the file and drag 'n drop the folder to where you want, say, Desktop)

Open a terminal (command line)

Go to the location you extracted the alsa-driver folder (if you did it on Desktop, type cd /home/xxx/Desktop/alsa-driver/ where xxx is your user)

Type the commands one after the other ends:
./configure --enable-dynamic-minors
make
sudo make install-modules
sudo gedit /etc/modprobe.d/alsa-base (I replaced vim with gedit because it's easier)

copy and paste this:
options snd_hda_intel model=hp-dv5

save the file and restart your laptop

As I said, just did it (took me about 10-15 min.) and now Metallica is rocking on my system.

Good luck.
Greetings from Mexico City

Thankyou, Thankyou, Thankyou!! If only more people wrote their instructions in such a way - I now have sound, quiet but it's sound!!:P

---

### Post by the_guv on 2009-10-07
> **shinjimx said:**
> I've just did this on my dv2-1020la (Latinamerican version), worked like a charm.

What you have to do in simple steps:

go to this website:

[http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/)

Download the file alsa-driver-snapshot.tar.bz2

Go to your download location, extract it (I did it via the file manager, double click the file and drag 'n drop the folder to where you want, say, Desktop)

Open a terminal (command line)

Go to the location you extracted the alsa-driver folder (if you did it on Desktop, type cd /home/xxx/Desktop/alsa-driver/ where xxx is your user)

Type the commands one after the other ends:
./configure --enable-dynamic-minors
make
sudo make install-modules
sudo gedit /etc/modprobe.d/alsa-base (I replaced vim with gedit because it's easier)

copy and paste this:
options snd_hda_intel model=hp-dv5

save the file and restart your laptop

As I said, just did it (took me about 10-15 min.) and now Metallica is rocking on my system.

Good luck.
Greetings from Mexico City

hey *shinjimx .. *tx to you, i now have ACDC rocking my sys!

:guitar::guitar::guitar::guitar::guitar:

couple things tho .. for some folks, i think jaunty up

> sudo gedit /etc/modprobe.d/alsa-base (I replaced vim with gedit because it's easier)you may need to use "alsa-base.conf", rather than "alsa-base".

also ..

> copy and paste this:
options snd_hda_intel model=hp-dv5dunno if it's me or my setup, somehow, but for me it worked with hyphens rather than underscores, so i made that ..

options snd-hda-intel-model=hp-dv5

will re-post this on [this thread]("http://ubuntuforums.org/showthread.php?t=1043568&page=8") too (from where I found your post)

er, dunno about Metallica, mind ;)  call me old-fashioned.

---

### Post by DarkeKun on 2009-10-10
Hi, I got a serious problem, it dosnt detect my soundcard at all

"aplay: device_list:217: no soundcards found..."

I tried to update the drivers, so I could adjust the Microphone volume, and then it just droped my sound card.
How can I at least reset the drivers to default again?

---

### Post by DarkeKun on 2009-10-10
Problem solved, went on youtube, and got the answer

---

