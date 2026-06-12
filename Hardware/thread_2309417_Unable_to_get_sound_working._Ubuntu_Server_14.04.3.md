---
title: "Unable to get sound working. Ubuntu Server 14.04.3"
date: 2016-01-10
forum: Hardware
---

### Post by cgarz on 2016-01-10
Hello, I have had this problem for a while now. I have looked around in many places for solutions. But none have worked. Asking here since a few other similar questions were asked here.

The OS is running on an old Sony Vaio Laptop, model: VPCEB3F4E.

I have used the alsa information script to gather info.
Output is here: [http://www.alsa-project.org/db/?f=48f08f47664104fbec921ac7d0be4ca94be3ef35]("http://www.alsa-project.org/db/?f=48f08f47664104fbec921ac7d0be4ca94be3ef35")
When running the script the following is displayed before it saves the file:
```
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1590: No soundcards found...
cat: /tmp/alsa-info.2TnPpLYBxa/alsactl.tmp: No such file or directory
```

I have tried adding:
```
options snd-hda-intel model=auto
```
To the bottom of /etc/modprobe.d/alsa-base.conf but it doesn't help.

I have tried reinstalling the modules and alsa files using the large command:
```
sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
```

From [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
Except ofc editing it to remove desktop gui elements as I am on a server.

I have tried adding myself to the audio group.
I have tried deleting alsa-base.conf, purging alsa-base and reinstalling it.
I have tried looking in the bios to see if anything is disabled. But as with most laptop BIOS options, they suck. Only able to change time, boot order, and C3/C6 support for the CPU.

I have had some progress manually loading snd_hda_intel using:
```
sudo modprobe snd_hda_intel
```
That at least gets me an audio device and some more entries under /dev/snd but when playing a file its just static that I hear.

Any help and suggestions are appreciated. Thanks in advance =)

---

### Post by cgarz on 2016-01-10
I'm not sure how but it seems now that turning down the volume made the sound clear. I'm sure I tried messing with the sound before but oh well lol. Steps taken were as follows:

Manually loaded snd_hda_intel, accessed volume settings by typing alsamixer at the console and then turning down the volumes from the red area. 

These levels were then saved by issuing the command:
```
sudo alsactl store
```
The module was set to load at boot by adding
```
snd_hda_intel
```
to the list in:
```
/etc/modules
```
To do that I used nano:
```
sudo nano /etc/modules
```
And then rebooted. Sound now working from boot =D

---

