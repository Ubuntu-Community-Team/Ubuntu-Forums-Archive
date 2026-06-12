---
title: "Acer Aspire Sound problems"
date: 2009-01-17
forum: Hardware
---

### Post by ZioNemo on 2009-01-17
Hi,
I have an Acer Aspire 8930.
lspci says I have:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I have found and used the various helps floating around for Acer Aspire.
I followed directions and, in particular:
[LIST=1]
[*]I upgraded alsa drivers to version: alsa-driver-1.0.18a  alsa-lib-1.0.18  alsa-utils-1.0.18
[*]I added "options snd-hda-intel model=acer" to /etc/modprobe.d/alsa-base
[*]I downloaded and compiled  hda-verb-0.3
[*]I added "/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2" to /etc/rc.local
[/LIST]
Now I do have some amount of sound, but:
[LIST=1]
[*]The volume is extremely low even at 100% setting
[*]The internal microphone is not working.
[*]I also tried to upgrade alsa with module-assistant(see: <https://help.ubuntu.com/community/AspireOne>), but compilation fails in acore/info.c.
[/LIST]
Can someone help me setting up this thing in a sensible way?
My target is to be able to use Skype on this PC so I can avoid dual-booting; I thus need Audio and Mic (I can do without the video).

Please please help me.

TiA
ZioNemo

---

### Post by Miedzinjsh on 2009-03-18
I have tried the same way and have the same situation....
any ideas?

---

### Post by manolomanolo on 2009-03-19
Same problem with Acer Aspire 5730z.Volumes are at top levels as shown by alsamixer. Also, the ubuntu startup sound "jumps".

I realized sound problems with Skype had been solved by killing pulseaudio process and restaring Skype. Then I removed pulseaudio.

As for microphone, double click on the "Volume Control" icon next to the clock on the upper pane. Click on Preferences and activate all of the options, especially microphone options. Then go to Playback tab, activate microphones and set the volumes. **Then go to Options tab and select "Front Mic" into the Input Source field**

---

### Post by paintbalforjesus on 2009-04-02
I have a friend who has a similar problem.  He has an Acer Aspire 5920G which I installed ubuntu on for him and he says the sound is very low compared to its volume in windows from the internal speakers.  Also, when the computer goes to sleep the sound stops altogether and he has to restart the computer to get it to work again.  Any ideas?

---

### Post by brolin_1911a1 on 2011-08-24
I have an ACER 5552-3691 with Intel HDA ATI SB running dual boot under Natty Narwhal and Win7.  Whenever I boot into Linux, it defaults to no sound from the internal speaker but I do have sound from the external speaker jack.  I have to go into alsamixer every time and raise the volume for the built-in speaker in order to hear anything.  Then, the next time I reboot into Linux, the same situation repeats.

How do I get it to remember the settings so that I don't have to enable sound each time I reboot?

---

