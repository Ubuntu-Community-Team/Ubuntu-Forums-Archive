---
title: "Acer Aspire 5100 Problem - No input signal from line-in or microphone"
date: 2010-05-15
forum: Hardware
---

### Post by rhymeface on 2010-05-15
Hi all,

I'm running Ubuntu 9.10 Karmic on an Acer Aspire 5100 and I can't get either the built in microphone or the line-in to work.

Assuming this isn't some hardware failure, can someone point in the right direction to get either of the two working. Line-in would be more useful to me than the microphone.

I checked this thread,

[http://ubuntuforums.org/showthread.php?t=623092](http://ubuntuforums.org/showthread.php?t=623092)

But it's for an old version of Ubuntu and was relevant to how the sound controls are set up on 9.10 (or at least, I couldn't see how to apply the info).

Any help would be greatly appreciated.

---

### Post by Bucky Ball on 2010-05-15
Pulseaudio? Applications->Sounds and Video->Pulse Audio Device Chooser. Left click the icon, Volume Control and start a playback stream. Right click it and 'Move Stream'.

---

### Post by rhymeface on 2010-05-15
> **Bucky Ball said:**
> Pulseaudio? Applications->Sounds and Video->Pulse Audio Device Chooser. Left click the icon, Volume Control and start a playback stream. Right click it and 'Move Stream'.
I don't have Pulse Audio in the list of applications.

---

### Post by rhymeface on 2010-05-17
Bump

---

### Post by lidex on 2010-05-18
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

### Post by Mylation on 2010-06-13
```
jeff@jeff-laptop:~$ uname -a
Linux jeff-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
jeff@jeff-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jeff@jeff-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
jeff@jeff-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2bfa
jeff@jeff-laptop:~$ 
```

Here's my output. My microphone seems to work after I restart my system but stops working after a random period of time.

---

### Post by lidex on 2010-06-13
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
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

### Post by thmonkey on 2010-10-07
rhymeface, did you manage to solve your problem? i have the same issue...

thanks!

---

### Post by DutchieR on 2011-02-04
Exact same machine, Aspire 5100, Ubuntu 10.10 latest build.
Latest version Skype (Beta) 2.1.0.81

Did all the things above, no result
Still same problem, Skype test call records nothing.

But also cannot change any setting in Skype Sound Devices options which are all set to PulseAudio Server (local).

All the settings above seem to use ALSA as sound server so I guess I have to convince Skype to use ALSA, but how? (BTW, sound output is OK, even if Skype is configured for PulseAudio).

Suggestions?

---

