---
title: "No sound - Sony VAIO laptop VPCEB26GM/BI"
date: 2010-08-03
forum: Hardware
---

### Post by Kanichiro on 2010-08-03
I just installed Ubuntu 10.04 (64-bit) on my new Sony VAIO laptop. Everything seems to be working except I have no sound through either the speakers or using headphones. This is actually a duel-boot machine (Ubuntu 10.04 (64-bit)/Windows 7).  I've updated everything, turned the sound up all the way without success. I do have sound on Windows, it just does not work on Ubuntu.

---

### Post by maciej234 on 2010-08-03
try searching this site.  I had a similar problem on my iMac but the volume was very low.  I had to edit a text file using gedit.  You could also try checking the alsa mixer via the terminal.  I think the command is alsa mixer; make sure the volume is up

---

### Post by Kanichiro on 2010-08-03
> **maciej234 said:**
> try searching this site.  I had a similar problem on my iMac but the volume was very low.  I had to edit a text file using gedit.  You could also try checking the alsa mixer via the terminal.  I think the command is alsa mixer; make sure the volume is up


Here is the content of my alsa.base.conf file:
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

---

### Post by utilitytrack on 2010-08-03
to **Kanichiro**

Ok, please learn right ask questions. Put on forum more diagnostics info. Try it:
   
```
$ uname -r

$ dpkg -l alsa-*

$ lspci -nn | grep Audio

$ cat /proc/asound/card0/codec#0 | grep Codec

# hwinfo --sound

$ cat /etc/modprobe.d/alsa-base.conf (it's you gave us, ok)

```

---

### Post by Kanichiro on 2010-08-03
Maybe this might help.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kanichiro@kanichiro-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
kanichiro@kanichiro-laptop:~$ head -n 1 /proc/asound/card*/codec#*

---

### Post by utilitytrack on 2010-08-04
It's not it that I asked

---

### Post by Kanichiro on 2010-08-04
> **utilitytrack said:**
> It's not it that I asked

Sorry, then I do not understand what you are looking for. I just want to get my sound working.

---

### Post by utilitytrack on 2010-08-04
I'm so sorry, Mr. Kanichiro! I'm so sorry, but I asked you some technical info for mode deep understand your problem. If you can't give (or don't wish give) this info please say about it, ok?

---

### Post by Kanichiro on 2010-08-05
> **utilitytrack said:**
> I'm so sorry, Mr. Kanichiro! I'm so sorry, but I asked you some technical info for mode deep understand your problem. If you can't give (or don't wish give) this info please say about it, ok?

I do not know what info you require or how to get it.  If you can tell me how to get this info I will gladly post it for you.

---

### Post by utilitytrack on 2010-08-06
> **Kanichiro said:**
> I do not know what info you require or how to get it.  If you can tell me how to get this info I will gladly post it for you.

Ok, simply to ensure that no one spoke me that I'm monkey, I with pleasure to repeat: for to solve any problem with hardware you should post on this forum some diagnostical info. What exactly in that case:

```
$ uname -r
$ dpkg -l alsa-*
$ lspci -nn | grep Audio
$ cat /proc/asound/card0/codec#0 | grep Codec
# hwinfo --sound
$ cat /etc/modprobe.d/alsa-base.conf (it's you gave us, ok)
$ cat /proc/asound/devices
```

also don't forget recheck levels in [FONT="Courier New"]alsamixer[/FONT]

Hint: you need to open terminal to run these commands. Look in here how to make it: [https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

### Post by Kanichiro on 2010-08-06
Utilitytrack,
Thank you very much for your help!  I've attached a text file with the code returns. I hope this includes all the information you requested. Please let me know if there is anything else you need to help solve my sound problem. 

Kanichiro

---

### Post by utilitytrack on 2010-08-06
Why you don't post all output to this forum? First, attachments it's inconvenient, second you forget about [FONT="Courier New"]hwinfo --sound[/FONT] (this command required root's privileges). Run it or say me which sound module do you use (I guess that is snd-hda-intel probably).

---

### Post by Kanichiro on 2010-08-06
> **utilitytrack said:**
> Why you don't post all output to this forum? First, attachments it's inconvenient, second you forget about [FONT=Courier New]hwinfo --sound[/FONT] (this command required root's privileges). Run it or say me which sound module do you use (I guess that is snd-hda-intel probably).


kanichiro@kanichiro-laptop:~$ uname -r
2.6.32-24-generic
kanichiro@kanichiro-laptop:~$ dpkg -l alsa-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  alsa-base      1.0.22.1+dfsg- ALSA driver configuration files
un  alsa-oss       <none>         (no description available)
ii  alsa-tools     1.0.22-0ubuntu Console based ALSA utilities for specific ha
ii  alsa-tools-gui 1.0.22-0ubuntu GUI based ALSA utilities for specific hardwa
ii  alsa-utils     1.0.22-0ubuntu ALSA utilities
kanichiro@kanichiro-laptop:~$ lspci -nn | grep Audio
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
kanichiro@kanichiro-laptop:~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC269
kanichiro@kanichiro-laptop:~$ cat /etc/modprobe.d/alsa-base.conf
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
kanichiro@kanichiro-laptop:~$ cat /proc/asound/devices

Yes, I believe the sound module is  snd-hda-intel.

---

### Post by utilitytrack on 2010-08-06
When you discuss such questions as troubles with hardware you shouldn't speak "I believe" or "I don't believe". These problems require exactly answers. 

Ok, I think that upgrade ALSA might help in your case because:
> ALSA: hda - Add fix-up for Sony VAIO with ALC269([http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23#HDA_Codec_driver]("http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23#HDA_Codec_driver")). 

Please follow instructions on [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810") and post here your impressions. Or don't post.

---

### Post by Kanichiro on 2010-08-06
> **utilitytrack said:**
> When you discuss such questions as troubles with hardware you shouldn't speak "I believe" or "I don't believe". These problems require exactly answers. 

Ok, I think that upgrade ALSA might help in your case because:
([http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23#HDA_Codec_driver](http://www.alsa-project.org/main/index.php/Changes_v1.0.22_v1.0.23#HDA_Codec_driver)). 

Please follow instructions on [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) and post here your impressions. Or don't post.

The upgrade instructions you provided worked.  I now have sound. 

Thank you very much!

---

### Post by utilitytrack on 2010-08-06
Yes. Please mark this thread as solved.

---

