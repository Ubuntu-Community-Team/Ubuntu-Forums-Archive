---
title: "Dell E1705 WEIRD subwoofer and speaker issues"
date: 2010-05-17
forum: Hardware
---

### Post by ronzorelli on 2010-05-17
Hey folks. New convert to linux here.

I just installed Ubuntu on my Dell E1705 after vista began to flake out much more than normal. 

Everything is working stellar... except this one issue.


The intel sound drivers appear to be working, but the issue is that when the sound is low, the speakers don't work, but the subwoofer does. ALL the sound at low volumes on the slider comes out of the sub, not the main speakers. They light up with sound when you get about 1/3 of full volume on the slider.

Anyone else run into this? If so, what worked for you?

---

### Post by lidex on 2010-05-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags.

---

### Post by ronzorelli on 2010-05-18
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags.

Linux ron-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
ron@ron-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ron@ron-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
ron@ron-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9200

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa

---

### Post by lidex on 2010-05-18
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m27 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by ronzorelli on 2010-06-01
I've played with the settings and it's still doing exactly the same thing.

---

### Post by lidex on 2010-06-01
Then I would suggest an alsa upgrade via the alsa-upgrade link in my sig.

---

### Post by ronzorelli on 2010-06-15
> **lidex said:**
> Then I would suggest an alsa upgrade via the alsa-upgrade link in my sig.

I did that. Made no difference, honestly.

But now, after system updates through Ubuntu, I have no sound at all. It doesn't even recognize that I have any type of sound devices at all.

Between this and the online video/loss of wireless issue I have going on as well, I'm pretty frustrated with this OS and my lack of knowledge of it. 

I'm having a hard time not going back to what I know...

---

### Post by lidex on 2010-06-16
Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

What is this output:
```
dpkg -l | grep "alsa"
```

---

### Post by ronzorelli on 2010-06-16
> **lidex said:**
> Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

What is this output:
```
dpkg -l | grep "alsa"
```

rm: cannot remove `/etc/asound.conf': No such file or directory

---

### Post by lidex on 2010-06-16
> **ronzorelli said:**
> rm: cannot remove `/etc/asound.conf': No such file or directory

That's fine. Not present on all systems.
How about the other results?

---

### Post by ronzorelli on 2010-06-16
> **lidex said:**
> That's fine. Not present on all systems.
How about the other results?

ii  alsa-base                                                1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                                    1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                                 1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                              1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                               1.0.22-0ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                           1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                                               1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                                             0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard driver
ii  alsaplayer-alsa                                          0.99.80-5                                       PCM player designed for ALSA (ALSA output module)
ii  alsaplayer-common                                        0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-daemon                                        0.99.80-5                                       PCM player designed for ALSA (non-interactive version)
ii  alsaplayer-esd                                           0.99.80-5                                       PCM player designed for ALSA (EsounD output module)
ii  alsaplayer-gtk                                           0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  alsaplayer-jack                                          0.99.80-5                                       PCM player designed for ALSA (JACK output module)
ii  alsaplayer-nas                                           0.99.80-5                                       PCM player designed for ALSA (NAS output module)
ii  alsaplayer-oss                                           0.99.80-5                                       PCM player designed for ALSA (OSS output module)
ii  alsaplayer-text                                          0.99.80-5                                       PCM player designed for ALSA (text version)
ii  alsaplayer-xosd                                          0.99.80-5                                       PCM player designed for ALSA (osd version)
ii  balsa                                                    2.4.1-1                                         An e-mail client for GNOME
ii  bluez-alsa                                               4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                                       0.10.28-1                                       GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa                                     1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsox-fmt-alsa                                          14.3.0-1.1build1                                SoX alsa format I/O library

---

### Post by lidex on 2010-06-17
Try the alsa-upgrade link in my sig.

---

### Post by ronzorelli on 2010-06-17
> **lidex said:**
> Try the alsa-upgrade link in my sig.

That was my first move after the audio went away the first time. I've done the update twice since then. Within one or two days of running the update, I get a notice from Ubuntu that there are updates available. I install them all because I don't know Ubuntu well yet, and BAM! The audio is gone again after the 'updates'.

---

### Post by lidex on 2010-06-17
Unfortunately...
> Ubuntu upgrades/updates might overwrite your Alsa installation once in a while (e.g. Major upgrades, kernel-upgrades or ALSA-package upgrades).
You just need to rerun the upgrade-script using the -i option in this case (if you still have the compiled sources on the disk). 

---

### Post by ronzorelli on 2010-06-17
Guess I missed that part... *sigh*

Thanks.

---

### Post by AjaxVCU on 2010-08-09
I'm having the same problem with my sound.  I never lose sound entirely but I'm only getting sound out of the sub-woofer.  I've upgraded the driver with the script mentioned above.  I've tried messing with the alsamixer but no matter what I change it goes back once I adjust the volume.  Any help here would be greatly appreciated.

---

### Post by lidex on 2010-08-09
> **AjaxVCU said:**
> I'm having the same problem with my sound.  I never lose sound entirely but I'm only getting sound out of the sub-woofer.  I've upgraded the driver with the script mentioned above.  I've tried messing with the alsamixer but no matter what I change it goes back once I adjust the volume.  Any help here would be greatly appreciated.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

