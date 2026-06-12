---
title: "Gateway NV52 Interal Mic"
date: 2010-03-03
forum: Hardware
---

### Post by adam22 on 2010-03-03
Does not work. I posted about this a while ago, but have since reinstalled Ubuntu and am trying to again. 

All signs point to going to [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) and downloading the deb package. I do this, and when I restart, I get a popping noise whenever I open applications and the internal mic still does not work. The popping is so annoying, hard to explain.....can anyone help me out here?

---

### Post by adam22 on 2010-03-14
So...any ideas?

---

### Post by PhazzedOut on 2010-05-15
Bump

---

### Post by cnja on 2010-05-16
I have the same laptop, and had the same issue.  after much fussing and cussing, and reloading etc... i stumbled upon dumping pulseaudio and loading ALSA...  seemed to work.
apparently there is a known bug in pulseaudio but some people are still pushing it as the defacto in controlling the audio in linux.   Hope this helps.

---

### Post by lidex on 2010-05-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
cat /etc/modprobe.d/alsa-base.conf

```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags.

---

### Post by asoltys on 2010-08-28
Same laptop, same problem, mic not working.  I just installed pulseaudio to get my speakers working, which they are now, so I'm reluctant to go back to just alsa.  Here's the output of those commands:


```
$ uname -a
Linux A317641 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jul  6 2010 for kernel 2.6.32-24-generic (SMP).
adam@A317641:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20561 (Hermosa)

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI


$ cat /etc/modprobe.d/alsa-base.conf 
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
```

---

### Post by lidex on 2010-08-28
> **asoltys said:**
> Same laptop, same problem, mic not working.  I just installed pulseaudio to get my speakers working, which they are now, so I'm reluctant to go back to just alsa.  

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by adam22 on 2010-09-05
I had forgotten about this thread, I never did fix the mic issue.

```
Linux adam-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
adam@adam-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
adam@adam-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
adam@adam-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20561 (Hermosa)

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
adam@adam-laptop:~$ cat /etc/modprobe.d/alsa-base.conf
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

```

Should I go ahead and try the above directions?

---

### Post by lidex on 2010-09-05
> **adam22 said:**
> I had forgotten about this thread, I never did fix the mic issue.

Should I go ahead and try the above directions?

I would suggest the alsa-base.conf edit I posted above after upgrading your alsa install via the link in my sig.

---

### Post by adam22 on 2010-12-30
Just an update...this worked perfectly. Thanks again.

---

### Post by pouchette on 2011-01-09
[COLOR=Blue][SIZE=3]:(  Not solved...

the post was about speakers sound problem : external and internal sources working together ; external speakers and internal headphones output playing sounds...

and the post 'there' was about micro device not working..

or maybe I didn't well understand the issue of the process indicated in this post there related to this one ?

which invites to do :

[/SIZE][/COLOR] gksudo gedit /etc/modprobe.d/alsa-base.conf
[COLOR=Blue][SIZE=3]
[/SIZE][/COLOR] options snd-hda-intel model=laptop position_fix=1 enable=yes
[COLOR=Blue][SIZE=3] I have a pb of output devices (internal and external spk) not a pb of input with microphone device, so what should I do ?
    
usually when you plug micro in the jack entry, external sound from speakers should automatically shut down.. which is not happen to my computer and so I don't know how to solve that pb..

thanks for your help..
[/SIZE][/COLOR]

---

### Post by lidex on 2011-01-09
@pouchette
Do me a favor and start a new thread describing you problem concisely and also post the link to your alsa-info following this procedure:
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]
Then PM me the link to the new thread.

---

### Post by jcreneau on 2011-02-06
I have a Gateway CX2724 and can't get the mic working even with this fix.  Any ideas?

> [02:16 PM john ~]$ uname -a
Linux john-laptop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

[02:17 PM john ~]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[02:17 PM john ~]$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.

[02:17 PM john ~]$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9250

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054

[02:17 PM john ~]$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2


---

### Post by lidex on 2011-02-09
> I have a Gateway CX2724 and can't get the mic working even with this fix. Any ideas?
That fix was for different hardware so no surprise. Try this instead. ```
echo "options snd-hda-intel model=ref" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by jcreneau on 2011-02-09
Unfortunately, it looks like that didn't work.  Any other ideas?

Update - appending the following also does not seem to work (Ideas taken from [this thread]("http://ubuntuforums.org/showthread.php?t=314383"))
```
options snd-hda-intel probe_mask=1
```
```
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```


This also doesn't work (modified from [this thread.]("http://art.ubuntuforums.org/showthread.php?p=9815275"))
```
options snd-hda-intel model=ref probe_mask=1 position_fix=1
```

This also doesn't work (from ["Extra Hints to get sound working."]("https://help.ubuntu.com/community/HdaIntelSoundHowto"))
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```


Update (again):

When I use alsamixer to turn "mux" all the way up and have my headphones plugged into the microphone jack (don't have an external mic... ) in the front of the computer, I am able to record things but the volume is greatly muted.  Perhaps the external jack is set to default for the microphone instead of using the internal mic?

I also have the [output for alsa-info.sh]("http://www.alsa-project.org/db/?f=e5cd120004c7868cafa7d5dbad3458575d1271cf") if you want it - this was mentioned in the alsa configuration file (/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt).  Info about alsa-info.sh[here.]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")

---

### Post by lidex on 2011-02-15
> **jcreneau said:**
> Unfortunately, it looks like that didn't work.  Any other ideas?

Update - appending the following also does not seem to work (Ideas taken from [this thread]("http://ubuntuforums.org/showthread.php?t=314383"))
```
options snd-hda-intel probe_mask=1
```
```
options snd-hda-intel model=test enable-msi=1 probe-mask=1
```


This also doesn't work (modified from [this thread.]("http://art.ubuntuforums.org/showthread.php?p=9815275"))
```
options snd-hda-intel model=ref probe_mask=1 position_fix=1
```

This also doesn't work (from ["Extra Hints to get sound working."]("https://help.ubuntu.com/community/HdaIntelSoundHowto"))
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```


Update (again):

When I use alsamixer to turn "mux" all the way up and have my headphones plugged into the microphone jack (don't have an external mic... ) in the front of the computer, I am able to record things but the volume is greatly muted.  Perhaps the external jack is set to default for the microphone instead of using the internal mic?

I also have the [output for alsa-info.sh]("http://www.alsa-project.org/db/?f=e5cd120004c7868cafa7d5dbad3458575d1271cf") if you want it - this was mentioned in the alsa configuration file (/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt).  Info about alsa-info.sh[here.]("http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh")

These are the model switches for your codec:
```
STAC9202/9250/9251
==================
  ref		Reference board, base config
  m1		Some Gateway MX series laptops (NX560XL)
  m1-2		Some Gateway MX series laptops (MX6453)
  m2		Some Gateway MX series laptops (M255)
  m2-2		Some Gateway MX series laptops
  m3		Some Gateway MX series laptops
  m5		Some Gateway MX series laptops (MP6954)
  m6		Some Gateway NX series laptops
  auto		BIOS setup (default)
```

First you'll want to clean up any misc crap from alsa-base.conf.
Post this output please:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by jcreneau on 2011-02-15
I tried the model=ref switch as you suggested and browsed through the others but didn't try any of those.

Here's the ouput  
```
09:13 AM john /etc/modprobe.d]$ cat alsa-base.conf
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

---

### Post by lidex on 2011-02-16
How about this output:
```
ls /etc/modprobe.d/
```

---

### Post by jcreneau on 2011-02-16
Here you go:
```
[07:51 PM john /etc/modprobe.d]$ ls
alsa.backup     blacklist-ath_pci.conf  blacklist-firewire.conf     blacklist-modem.conf  blacklist-watchdog.conf            libpisock9.conf
alsa-base.conf  blacklist.conf          blacklist-framebuffer.conf  blacklist-oss.conf    intel-5300-iwlagn-disable11n.conf  oss-compat.conf

```

---

### Post by lidex on 2011-02-17
What are the contents of these two files:
```
cat /etc/modprobe.d/alsa.backup
cat /etc/modprobe.d/oss-compat.conf
```

---

### Post by jcreneau on 2011-02-17
alsa.backup is currently exactly the same as alsa-base.config (it's just the copy I made before I started messing around with the real one :))

```
[10:37 PM john /etc/modprobe.d]$ cat /etc/modprobe.d/alsa.backup
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
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

```

```
[11:02 PM john /etc/modprobe.d]$ cat /etc/modprobe.d/oss-compat.conf
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }
```

---

### Post by lidex on 2011-02-17
Humor me and move the alsa.backup file out of that directory please. Then reboot and post a new alsa-info result.

---

### Post by jcreneau on 2011-02-17
Done and done:


```
[11:42 PM john /etc/modprobe.d]$ ls
alsa-base.conf          blacklist.conf           blacklist-framebuffer.conf  blacklist-oss.conf       intel-5300-iwlagn-disable11n.conf  oss-compat.conf
blacklist-ath_pci.conf  blacklist-firewire.conf  blacklist-modem.conf        blacklist-watchdog.conf  libpisock9.conf

```

[http://www.alsa-project.org/db/?f=e40cf0ce898066bda04055dd5aff18ff222a902d](http://www.alsa-project.org/db/?f=e40cf0ce898066bda04055dd5aff18ff222a902d)

---

