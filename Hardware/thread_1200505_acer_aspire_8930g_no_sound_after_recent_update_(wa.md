---
title: "acer aspire 8930g no sound after recent update (was working before)"
date: 2009-06-30
forum: Hardware
---

### Post by hamfletta on 2009-06-30
Hey guys. Im having issues with my 8930g laptop. Sound was working fine (alsa) but i did a update this morning and have lost all sound :(

To get it working before i use the hda-verb trick as well as setting my model to be acer-aspire. This now does not work. I have tried to recompile and reinstall hda-verb but no dice.

```
adam@adamwork-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I also had problems with my graphics but after a re-install of the nvidia drivers that is now working again.

Any ideas on how i can fix this? Anyone else haveing the same issues?

Adam

---

### Post by Pratt on 2009-07-05
I am a complete newbie to Linux of any variety and have no sound on my Acer Aspire 8930g running Ubuntu 9.04.  I have fiddled around with all sorts of slides. everything from the Gnome Alsa mixer to Rhythmbox to Movie player.  I went to System - Preferences -Sound, and played around with all sorts of combinations of Devices, as well as 'autodetect' but nothing.  I left it on Generic 10 de OSS mixer at the moment. I have a box come up with:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

amongst a load of other boxes as equally negative!

I am baffled.   The console lights up on the keyboard, I have streaming video through Firefox - no sound.  I have bbc iplayer - with no sound.  Can anyone help me with my problem please?  I have searched for the last three days for a solution, but I can't seem to find one, although I think that maybe I couldn't recognize it even if I saw it, having had no experience with Linux and niether do I know anyone who has had experience with it either.  I think I'm in too deep here, maybe Vista is all I can use!!!  Thank you for your time (if you spent any reading this).

---

### Post by ivanvajar on 2009-07-05
Post output of> gksudo gedit /etc/modprobe.d/alsa-base.conf

Google about 'sound on *whatevercomputeryouareusing*
It's a matter of adding few lines at the end /etc/modprobe.d/alsa-base.conf in most cases

---

### Post by Patricrawley on 2009-08-21
I have found that the latest snapshot of the ALSA drivers works very well on the 8930g. All my speakers work with no hda verb alongside. All you have to do is download the ALSA upgrade script from the thread that I have linked below. Then execute it by doing this after opening the directory it is saved in in your terminal:
```

sudo ./ALSA* -snap

```

[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

After that is done and before you restart, change the line in your /etc/modprobe.d/alsa-base.conf from "options snd-hda-intel model=acer-aspire" to "options snd-hda-intel model=acer-aspire-8930g". After changing this line, save the file and restart your system and your sound should now be working.

---

### Post by hamfletta on 2009-09-03
The new version of alsa works a treat (as long as you use the alsa update script). Tried manually installing the new version of alsa but that did not work.

Interestingly my sound will not work unless i keep the HDA verb in the rc.local. Not sure why, might be due to my attempt to manually upgrade alsa.

Anyway thanks for the tips. 

Adam

---

### Post by jlk70 on 2009-10-22
Okay I am way to dumb.  I need very simple instructions, for a windows guy who is trying Ubuntu for the second time.  How do I get my sound to work?  I understand getting into the terminal and thats about it.  :confused:

---

