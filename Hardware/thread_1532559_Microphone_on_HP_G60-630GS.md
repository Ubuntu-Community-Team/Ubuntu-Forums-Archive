---
title: "Microphone on HP G60-630GS"
date: 2010-07-16
forum: Hardware
---

### Post by Ben2r25 on 2010-07-16
My friend has a new HP G60-630GS. I installed Ubuntu 10.04 on it and everything seems to work except the built in microphone, and I'm trying to set up skype. Any ideas?

---

### Post by AltomineUK on 2010-07-16
Hello :D

Most likely the mic is in mute (well it was in my case....)

Go to your volume  icon (top-left of your screen)....click on 'Sound Preferences'. Then  select the 'Input' tab. You should find the setting for your mic. Unmute  it by unchecking the 'Mute' box. Adjust the volume to your comfort.  That should sort it out....

Skype also has a default setting that automatically reduces your mic  volume if your voice is too loud. For that you need to go into the skype  settings and disable the automatic mixer option, should you wish for it  to be disabled.

---

### Post by Ben2r25 on 2010-07-17
The mic was muted, but it still does not work even after being unmuted. I played around with its sensitivity settings, and I tried disabling Skype's ability to mess with the settings. I still can't get it to work. I also tried using the sound recorder in ubuntu to see if it was just a skype issue, but that doesn't work either.

---

### Post by AltomineUK on 2010-07-18
Right...... Try this.... 

[http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/](http://www.blog.arun-prabha.com/2008/05/23/skype-microphone-problem-and-complete-pulse-audio-setup-in-ubuntu/)

---

### Post by lidex on 2010-07-18
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Ben2r25 on 2010-07-19
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

Alsa mixer now shows mic b, c, d, e, and f. They are all off except for b. However mic b is shown in red and has no level. capture is set to 100. As for sound cards, the only choice is HDA Intel. The internal mic is still not working. I double checked and it is not muted.

---

### Post by lidex on 2010-07-19
Try only using one of those lines at a time - try both of them alone.

---

### Post by Ben2r25 on 2010-07-19
> **lidex said:**
> Try only using one of those lines at a time - try both of them alone.

When using just the first line and checking alsamixer in the terminal, everything appears the same as when I use both lines. I also noticed that the capture is in red along with mic b. I double checked and this is also true when I use both lines.

When using just the second line there is no mic b-f and capture is still in red. I tested both setups with sound recorder to make sure, and neither works.

---

### Post by lidex on 2010-07-19
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Ben2r25 on 2010-07-19
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

```
nicole@nicole-laptop:~$ uname -a
Linux nicole-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
nicole@nicole-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nicole@nicole-laptop:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-22-generic 2.6.32-22.13                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-2.6.32-23-generic 2.6.32-23.16                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.23.24                                    Backported drivers for alsa-driver snapshot.
nicole@nicole-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20583 (Pebble HSF)

==> /proc/asound/card0/codec#2 <==
Codec: Intel G45 DEVCTG

```

This laptop is an HP G60-630US. Thanks for the help.

---

### Post by lidex on 2010-07-19
It should be working at this point. I'm at somewhat of a loss. I would suggest removing the alsa-backports you have installed. Next reboot, then download and install the linuxant drivers.
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by phrenchax on 2010-07-21
ben2r25:
When you see the different mic options (a through d or whatever it is), Try turning up the volume on each of the mics one at a time and testing each one.  On my sister's laptop (HP G60 635 I think it was) the third or fourth one turned out to be the winner.

Good luck!

---

### Post by Ben2r25 on 2010-07-22
@lidex 
 
I removed alsa-backports (I had installed them to remedy an unrelated sound issue) and installed the linuxant generic deb package. That was unsuccessful, so I reinstalled alsa-backports leaving the linuxant driver installed...still no luck.

@phrenchax

I am able to switch the active mic with the GNOME ALSA mixer program (I can't seem to switch them in the terminal with alsamixer) however, I can't turn up any levels on any of the mics through alsamixer in the terminal (there isn't even a box that shows the level for the active mic) The only level shown is on the "CAPTURE" and I have that all the way up. Does capture work on the active mic or am I missing something? Anyway I tried activating and testing every mic in both configurations I explained above to lidex, and nothing's working yet.

---

### Post by lidex on 2010-07-22
I don't think you want to have linuxant and backports installed together. Did you remove entries from alsa-base.conf? If not it may conflict with linuxant and in that case remove backports and alsa-base entry. Now reboot and try again.

---

### Post by Ben2r25 on 2010-07-22
> **lidex said:**
> I don't think you want to have linuxant and backports installed together. Did you remove entries from alsa-base.conf? If not it may conflict with linuxant and in that case remove backports and alsa-base entry. Now reboot and try again.

I uninstalled backports again. I couldn't find the reference to backports in alsa-base.conf. Here is the text of my alsa-base file
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
#attempt to mute speakers when headphones are plugged in
options snd-hda-intel model=dell-vostro
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

#atempt at mic fix
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes
#options snd-hda-intel model="olpc-xo-1_5"
```

---

### Post by lidex on 2010-07-22
Remove these two lines and reboot:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

```

---

### Post by Ben2r25 on 2010-07-22
> **lidex said:**
> Remove these two lines and reboot:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

```

I removed the lines. While they are removed there is no sound at all on the laptop! alsamixer will not open in the terminal, and I am unable to access the controls using a graphical application either. Sound recorder won't open but skype and most other programs will.I tried rebooting to make sure it wasn't some kind of glitch. After putting those two lines back in it's back to how it was: sound is working and mic is not.

---

### Post by Ben2r25 on 2010-07-23
I just noticed that when I boot the computer with the lines in the file I get these two error messages

```
patch_cxtppch: Conexant HSF modem detected but driver not present
conexant_init: Conexant HSF modem detected but driver not present
```

---

### Post by Ben2r25 on 2010-07-24
I got it to work! I'm not sure exactly what did it. I reinstalled the drivers a few times. I got it to work with the linuxant drivers after activating mic f(maybe I overlooked this before but I was sure I tested everything.) One glitch though: Ubuntu just released an updated kernel which broke the linuxant driver since they were compliled on my machine. The mic no longer worked. I uninstalled the linuxant drivers and installed alsa backports (since they are kept up to date with the latest ubuntu kernel) and sure enough activating mic f works! It's a little scratchy but that's ok. Thanks for all the help

---

