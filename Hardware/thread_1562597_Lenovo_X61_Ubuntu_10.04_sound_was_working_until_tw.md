---
title: "Lenovo X61 Ubuntu 10.04 sound was working until two days ago (need debugging help)"
date: 2010-08-27
forum: Hardware
---

### Post by rocksockdoc on 2010-08-27
[B]What other sound debugging tools can I use to isolate where the problem lies?

[/B]I installed Ubuntu 10.04 on the Lenovo X61 tablet PC about a week ago and the sound worked fine. 

About two days ago, the sound just stopped. Nothing else seems amiss. No sound from the internal speakers and no sound is output to the headphones. Sound just stopped without any indication of why.

I would like to ask, since I'm brand new to Linux (although I'm not new to operating systems), for some debugging help when there is no sound.

Here's what I can tell you:
0. The "Gnome Indicator Applet 0.3.7" (System->Preferences->Sound) clearly shows the speaker icon with clear blue lines (no red x) indicating the "Sound Preferences" are not muted and the volume is set to a high level (and all indications when the panel is opened is that the sound output is working). Except there is no sound. :(

1. Since it was a new installation of the operating system, after updating Firefox to version 3.6.8, I added MP3 playing capabilities by running this in the URL window:
 apt:ubuntu-restricted-extras?section=universe?section=multiverse

2. To play encrypted DVDs, I then ran this in the terminal window:
    $ sudo /usr/share/doc/libdvdread4/install-css.sh

3. And, I followed recommendations to use VLC Media Player:
   Applications -> Ubuntu Software Center -> VLC Media Player -> Install

The sound worked just fine (fonts in VLC were another story but sound is the problem here). 

4. Maybe it was a mistake, but I also installed the libdvdcss2 package:
$ sudo apt-get install totem-xine libxine1-ffmpeg libdvdread4 &&
$ sudo /usr/share/doc/libdvdread4/install-css.sh

At some point, the sound stopped working. Looking back, it "might" have been when I installed the libdvdcss2 package (so my first question is how to back that out).

My main question is how do you debug the sound package on Ubuntu 10.04 on a Lenovo X61 tablet PC?

5. I did run the ubuntu audio tester[FONT=monospace] many times, but to no avail:
  $ [/FONT]ubuntu-bug audio

The "report" from that command indicates:
- Advanced Linux Sound Architecture Driver version 1.0.21
- card0 HDA Intel device 0 Analog Devices AD198x Analog
- card0 HDA Intel device 0 Analog Devices AD198x Digital

6. The volume level is set properly:[FONT=monospace]
  $ [/FONT]gnome-volume-control

7. It's not the media because the standard ubuntu test media doesn't play any sound:
    [FONT=monospace]$ [FONT=Verdana]aplay /usr/share/sounds/alsa/Front_{Center,Left,Right}.wav
[/FONT][/FONT]
8. I'm not in the "audio" group:
    $ fgrep -ie 'audio' /etc/group
    Reported: audio : 29 pulse
 
9. The system seems to recognize the sound card:[FONT=monospace]
  $ [/FONT]sudo aplay -l
   Reported:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

10. The sound modules seem to be installed:[FONT=monospace]
 $ [/FONT]find /lib/modules/`uname -r` | grep snd
  Reported scores of entries, e.g.:
/lib/modules/2.6.32-24-generic/kernel/sound/pci/snd-cs5530.ko
/lib/modules/2.6.32-24-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.32-24-generic/kernel/sound/pci/hda/snd-hda-intel.ko
etc.

11. The sound card seems to be physically installed (it was working just a few days ago):[FONT=monospace]
  $ [/FONT]lspci -v | less
Reported:
...stuff...
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
...stuff...

12. [FONT=monospace]The "alsa drivers" (whatever they are) seem to be ok:
   $ [/FONT]wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
Reported:
... stuff ... 
!!ALSA Version
Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22
... stuff ... 

**13. What other sound debugging tools can I use to isolate where the problem lies?**

---

### Post by IcarusR on 2010-08-28
Do you have a 'soft modem' that you do not use ? This can 'hog' sound cards.
Go to System > Administration > Hardware Drivers and deactivate the "Software modem" device.

Do a google search for "sound stopped working ubuntu"

---

### Post by rocksockdoc on 2010-08-28
> **IcarusR said:**
> Do you have a 'soft modem' that you do not use ?"

Thanks for trying to help. I resolved the problem. I'm not sure exactly how because I fiddled with MANY things (as shown above). 

I "think" what resolved it was going to "System->Preferences->Sound" as I had many times before, going to the "Hardware" tab, setting the "Choose a device to configure" to "Internal Audio 1 Onput Analog Stereo Output", and then setting the "Settings for the selected device" profile to "Analog Stereo Output". 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=167707&stc=1&d=1283003465[/IMG]

---

