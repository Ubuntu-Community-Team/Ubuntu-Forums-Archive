---
title: "Headphones have no sound! Help appreciated..."
date: 2009-01-21
forum: Hardware
---

### Post by phantom3113 on 2009-01-21
Hello community,

I had put a thread up about my problem a while ago, but got no replies, so I may have put it in the wrong section. Well, here goes:

Since upgrading to Intrepid (Clean install from Hardy) I've noticed a problem with my headphone jack, referred to as the "front" by my laptop. Once the computer is turned on and logged in and everything, the "front" vanishes [isn't recognized by the computer] UNLESS I have my headphones plugged in prior to boot up.

To clarify, (and somewhat reiterate) if I have my headphones inserted into the jack and *then* boot up, there will be sound coming out of them. If I plug them in *after* booting up, no sound comes through. To add to this, if I follow the first option but remove the headphones at any point while the computer's on and try to plug them back in, they won't work.

I've tried installing PulseAudio and doing all those sound mixing things, but I don't have the problem of sound coming out of both the headphones and the speakers. Does anyone have any idea why this is happening?

Also, my headphones have a regular headphone jack, NOT a usb.

---

### Post by markbuntu on 2009-01-22
The most likely problem is that you need to add the proper option for your hda sound chip. There are links for how to  figure that out in the Drivers/HDA section here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by phantom3113 on 2009-01-22
Boy, if I had a dollar for everytime I was guided to that thread :P. I tried the one route on there that I had overlooked before, but nothing improved. I posted a more in depth help-request on the end of it (the one that deals with speaker/headphone issues) since I found another person with an identical problem. However, if you have any more tips, I'll gladly hear them :)

---

### Post by markbuntu on 2009-01-22
We need some specific info about your hardware since this is a very hardware specific problem. We need the make and model of your pc and the result of aplay -l before we can even begin to help you.

---

### Post by phantom3113 on 2009-01-22
Oh, right. :P I posted it in the other one, but forgot to put it here. Ok, here goes:

Computer: Gateway T-1621

aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

This was asked in a related thread:

head -n 1 /proc/asound/card0/codec*:
```
==> /proc/asound/card0/codec#0 <==
Codec: SigmaTel STAC9205

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

```

The thread that the previous code refers to went about adding an option under the alsa-base...text? (I'm not sure what it's called) Basically, I was supposed to put in option sda-hda-intel model=[MODEL] and putting in one of the options that appeared under my card model on the alsa configuration.txt file. I tried them, but there was no improvement. If you need any more information let me know. Thanks!

---

### Post by markbuntu on 2009-01-22
I found this option that is reported to work for the Gateway T-1616. I do not know if the 1621 is the same soundwise but you can give it a try if you haven't already.

T-1616 

options snd_hda_intel model=dell-m42

---

### Post by phantom3113 on 2009-01-22
That is one of the one's that I had tried. I didn't try the other two underneath it (dell-m43, m44) because I thought they wouldn't do anything since they were so similar, and I didn't want to keep rebooting my computer so many sequential times. Do you suggest I try m43 and m44?

---

### Post by markbuntu on 2009-01-22
I suggest you keep trying things until you find the one that works but unless you feel a real urgency for doing this you could just try a different setting each time you shutdown on a normal basis. Just keep notes and let us know how you make out.

---

### Post by phantom3113 on 2009-01-22
Hopefully I can remember to do this before I shutdown each time. :P Thanks for the help and I'll let you know how I make out

---

### Post by phantom3113 on 2009-01-24
Alright, I've tried the different codecs, and here are the following outcomes:

dell-m42 --> No change in situation
dell-m43 --> regular laptop speakers didn't work at all
dell-m44 --> No change in situation

These were the only codecs listed for the number that matched my soundcard, STAC9205. Would codecs for a different model number work? Also, under volume control it lists the card (when referring to front:0) as STAC92xx:Analog and the main tab is listed as HDA ATI SB as opposed to HDA INTEL SB. Would that make a difference?

---

### Post by phantom3113 on 2009-01-27
Makin' a bump

---

### Post by brack on 2009-01-30
The same thing here with the desktop. Plug in headphones, reboot, sound is there, change headphones (unplug and plug in again) sound is slowly vanishes, and there is no way to restore it until next reboot. Logout doesnt help, need full reboot. After aplay -l get the following:
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
EDIT: The following helps temporary to avoid full reboot (one of the things I like about linux):
```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

```

---

### Post by phantom3113 on 2009-01-31
Looking at this, it's starting to appear that somethings askew with the STAC92xx line of sound cards (or whatever it is).

> EDIT: The following helps temporary to avoid full reboot (one of the things I like about linux):
Code:

killall pulseaudio

sudo alsa force-reload

pulseaudio -D


when you say this is a "temporary" fix, how long is temporary?

---

### Post by brack on 2009-02-01
"temporary" means till next unplug event

---

### Post by phantom3113 on 2009-02-02
Gotcha. I tried this out and it worked beautifully! This may not be a permanent fix, but at least it's something. Thanks!

---

### Post by WylieE on 2009-03-04
Thanks!  This fix helped me, temporary is better than no sound.

---

### Post by brack on 2009-04-08
But what about permanent solution?

I'm getting real tired form this problem, if ACCIDENTALLY unplug headphones and then plug them back right after, I get sound vanishing effect, like the one in amarok after pressing stop. This is not good at all, will somebody take care of it?

---

### Post by phantom3113 on 2009-04-09
I've put a bug report on launchpad a few weeks ago with a pretty detailed description, including the temporary "fix". So far, the bug status is still "new" and importance is "undecided". I'm hoping that this turns out to be a non-issue in Jaunty.

---

