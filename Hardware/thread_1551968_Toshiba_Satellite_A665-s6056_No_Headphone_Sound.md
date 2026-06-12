---
title: "Toshiba Satellite A665-s6056 No Headphone Sound"
date: 2010-08-13
forum: Hardware
---

### Post by Hallic7 on 2010-08-13
Hi!
I have a sound problem with my laptop. The speakers work nice but when I plug the headphones I can't hear anything. I'm using Ubuntu 10.04

Please help!!

---

### Post by dino99 on 2010-08-13
open synaptic and search for "tosh": you might install toshset and toshutils and fnfxd

about sound, install paprefs and gnome-alsamixer (set your prefs with it into 'apps sound alsamixer)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Hallic7 on 2010-08-13
Thanks for your reply dino99

I followed the instructions you gave me (installed toshset, toshutils, fnfxd, paprefs and gnome-alsamixer)  but the problem continues. In the Gnome Alsa Mixer there was no "apps sound alsamixer" in the preferences. I tried to follow the instructions on [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) but when I reached this part:

[INDENT]!!ALSA Version
!!------------

Driver version:     1.0.18
Library version:    1.0.18
Utilities version:  1.0.18[/INDENT]

I could not continue because in my file no driver, library or utilities version where specified, there was a variable instead.

What more can I try?

Thanks!!!

---

### Post by lidex on 2010-08-14
Stop! Do this!
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

### Post by Hallic7 on 2010-08-14
Hi! Thanks for the reply!!

The output of the commands goes like this:

**uname -a**
```
Linux Aralia 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686 GNU/Linux
```

**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

**dpkg -l | grep "alsa"**
```
ii  alsa-base                             1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                            1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                            4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.28-1                                       GStreamer plugin for ALSA
```

**head -n 1 /proc/asound/card*/codec#***
```


==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX
```

The model / make of my laptop is Toshiba Satellite A665-S6056

---

### Post by lidex on 2010-08-14
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by Hallic7 on 2010-08-14
Thanks for your quick reply!

I tried the suggested options, but the sound is not coming out of the headphones yet. I notice some strange things though:

1- When I select the correct sound card "0 HDA Intel" on AlsaMixer and close / restart the program, the "- (default)" option is always selected.

2- I removed the mute from the "Beep" and raise its volume. I can hear a sound on the headphones when I change the volume levels with my keyboard special keys, but all the other sounds do not work. 

3- In "System ->Preferences ->Sound" in the "Output" tag I only have one option to choose from which is "Internal Audio Analog Stereo" and in the "Hardware" tag only one device is present which reads "Internal Audio -  1 Output / 1 Input - Analog Stereo Duplex". I tried with all the profiles available with no success.

---

### Post by Marcelo Ruiz on 2010-08-14
I'm not an expert, but I had a similiar problem with a Toshiba M640.
Try to go to the realtek website and download the latest alsa pack: realtek-linux-audiopack-5.15
Follow UBUNTU instructions in the README file to install it.
I hope it helps!

Marcelo.

---

### Post by lidex on 2010-08-14
> **Hallic7 said:**
> 
3- In "System ->Preferences ->Sound" in the "Output" tag I only have one option to choose from which is "Internal Audio Analog Stereo" 

What about the 'Connector' option at the bottom of tab? Should be a dropdown selector with headphone option.

---

### Post by Hallic7 on 2010-08-15
Hi!! Thanks all of you guys for your help!!! :D

I tried the solution Marcelo Ruiz suggested and all is working great now!!!

Thanks a lot!!!!

---

### Post by cajunaggie on 2010-08-21
I tried searching the realtek website for the suggested file but I can't find it. Anyone know where I could get it?

---

### Post by Hallic7 on 2010-08-24
Hi!

The package can be found here...

[http://www.realtek.com/downloads/]("http://www.realtek.com/downloads/")

Select "High Definition Audio Codecs (Software)" then accept the notice, on the next page, at the bottom there is a "Unix (Linux)" section, download the file "Linux driver (2.6)" then unpack the archive and there is the "realtek-linux-audiopack-5.15" carpet. Inside you can find the readme.txt file with the instructions for Ubuntu.

---

### Post by cajunaggie on 2010-08-25
I've tried the realtek patch solution with no success

> **lidex said:**
> What about the 'Connector' option at the bottom of tab? Should be a dropdown selector with headphone option.

Which tab in particular are you talking about? I've looked everywhere I know where to look in the Sound Preferences menu and I can't find a 'Connector' tab anywhere.

---

### Post by Hallic7 on 2010-08-27
Hi, the exact steps I followed where all the mentioned in this thread. I think is VERY important to install the gnome alsa mixer for the realtek driver to work properly, so this where the steps that worked for me:

1- From Synaptic, search "tosh" and install "toshset" and "fnfxd". Then search and install "paprefs" and "gnome-alsamixer" (suggested by dino99)

2- Edit the file "alsa-base.conf" with this code 
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
``` and add this line at the bottom ```
options snd-hda-intel model=auto
``` Then check the volume levels in the alsa mixer with ```
alsamixer
``` This was suggested by lidex

3- After that, I tried what Marcelo Ruiz suggested in the #8 reply in this thread and all worked.

I did notice that if I install the drivers from realtek not following this steps it won't work, so maybe the same is happening for other users.

---

### Post by ralpyka on 2010-08-31
Hi
I have a Conexant sound card on a Toshiba L650, and the same problem(the headphone isn't working). I'm using Kubuntu 10.10. Can you help for me?

---

