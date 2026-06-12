---
title: "No sound with hp 6735s, ATI SBx00 Azalia (Intel HDA)"
date: 2009-03-06
forum: Hardware
---

### Post by green traffic cone on 2009-03-06
Evening All,
I'm rather an Ubuntu Noob, so please be gentle :)
I've just purchased an HP 6735s laptop and have installed Ubuntu 8.10. I'm not getting any sound through the speakers. Strange thing is it's fine through headphones.

I've played around with the audio settings and not been able to get anything, also tried *sudo apt-get install linux-backports-modules-intrepid-generic* with no improvement. I've asked around and no one seems to have any ideas. Oh and i know the speakers work as they are fine in Vista (sorry for the bad language).

lspci gives
*00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)*

any ideas would be gratefully received :)
cheers

---

### Post by dhcrawford on 2009-03-11
I"m having the same problem with a 6535b, any luck yet?

---

### Post by dhcrawford on 2009-03-11
Fixed!

Running 8.10

I am running ALSA exclusively and ran all the updates

I used this article as a basis for the fix:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

__________

edit /etc/modprobe.d/alsa-base

add at the end of the file:

options snd-hda-intel model=laptop

reboot
___________

Et Voila!

PS.  I spent the better part of a week trying to figure this out under Fedora.  It took me a few hours to get it right in Ubuntu.

---

### Post by green traffic cone on 2009-03-16
You're a genius! Worked first time and such a simple solution too. Start up music scared the living daylights out of me though. Anyway thanks for the help, I owe you one :)

---

### Post by lennyleonard on 2009-04-14
This also worked great on my HP Pavilion dv7 1245ca with the same sound card. Thanks very much! Ubuntu rules!

---

### Post by jaykemper on 2009-04-16
Ok this is weird, but it worked for me, and then a pop up window told be to set the default sound card by the command "asoundconf set-default-card".  The only card I have is "Intel" (output from "asoundconf list").  Now it doesn't work!

I can hear the login screen bongos, but the speakers stop working when I log in.  No start up music.  I think this means that it's a user setting that's screwed up.

I also added "options snd_hda_intel model=laptop" to the end of "/etc/modprobe.d/alsa-base"

Should I just uninstall all pulseaudio and alsa packages and user directories and start over again?

---

### Post by lennyleonard on 2009-04-17
If you double click the volume control icon, and choose "preferences", it allows you to choose more sliders for different inputs/outputs. Maybe one of them is muted by default, but not shown. That was the problem with my microphone input.

---

### Post by maron on 2009-05-29
I have problem with microphone at this soundcard. 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

I write code to '/etc/modprobe.d/alsa-base.conf' , but stil don't work.

---

### Post by chocobomastr on 2009-08-16
Worked for my HP 6535b as well

although I had to use

```
sudo gedit /etc/modprobe.d/alsa-base
```

in order to edit the file

This tweak is better than the suicide hotline

---

### Post by nigamp on 2009-11-11
hey thnx ,..this wrked 4 me ... :0:D

---

### Post by nigamp on 2009-11-11
hey thnx ,..this wrked 4 me ... :D

---

### Post by sroland81 on 2009-12-18
Sound is not working in HP 6735s and can't talk through Skype.... i followed steps above and i have no sound, no mic, no nothing... any ideas?

Regards,

---

### Post by uiteoi on 2010-01-10
I have been able to get audio playback working but not recording by installing the latest ALSA drivers using this script:
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

And adding at the end of /etc/modules the line:
snd-hda-intel

And rebooting.

$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

---

### Post by kronictokr on 2010-02-14
try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

---

### Post by JoWi on 2010-11-21
> **kronictokr said:**
> try this, has various fixes included, works like a charm

[http://swiss.ubuntuforums.org/showthread.php?t=1395089](http://swiss.ubuntuforums.org/showthread.php?t=1395089)

This link seems to be out-dated. Anybody knows an update?

---

### Post by Yuran321 on 2011-03-03
> **dhcrawford said:**
> Fixed!

Running 8.10

I am running ALSA exclusively and ran all the updates

I used this article as a basis for the fix:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

__________

edit /etc/modprobe.d/alsa-base

add at the end of the file:

options snd-hda-intel model=laptop

reboot
___________

Et Voila!

PS.  I spent the better part of a week trying to figure this out under Fedora.  It took me a few hours to get it right in Ubuntu.

Now it WORKS! 
Thank's!!!!!!

---

### Post by spennine on 2011-12-12
thank you dhcrawford, that HOWTO worked 4 me 2 :P

---

