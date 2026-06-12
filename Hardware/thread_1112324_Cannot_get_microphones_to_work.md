---
title: "Cannot get microphones to work"
date: 2009-03-31
forum: Hardware
---

### Post by TyrantWave on 2009-03-31
I'm having a bit of an odd error:
I'm trying to stream video via UStream, and I can get the webcam to work fine, however, I can't get the microphone to work.

I've tried both the mic that's part of the webcam (USB), and an external mic that connects to the microphone jack.

The computer detects the Webcam mic (It's alongside the USB Webcam, it has USB Audio). However, it doesn't detect the one connected the the jack at all.

I can't use the webcam mic even though it is detected - the sound settings consistently keep muting the mic no matter what I do, and no programs can actually run the mic, they just start error-ing.

I'm running Ubuntu 8.10 Hardy on a 1.6GHz, 1GB RAM Gateway laptop, if it helps.

---

### Post by TyrantWave on 2009-03-31
Bumpity bump

---

### Post by TyrantWave on 2009-03-31
Still can't get the laptop to even acknowledge the external mic =/.
The USB one's still being detected but doesn't actually do anything..

---

### Post by Ian Clark on 2009-04-01
I'm having a similar problem.  I just upgraded to Intrepid two days ago, and suddenly Audacity, Skype etc. programs that use a mic get no audio.  Everything is hooked up the way it was, but now my minicam and microphone aren't detected.  I've enabled the other panels in alsa preferences and nothing is muted.  Under preferences->sound the test for audio capture gives a loud click, but no tone.

Is there a way to point Intrepid to my microphone?

And off-topic, can I do the same for my webcam?

---

### Post by TyrantWave on 2009-04-01
Bumpity bump

---

### Post by markbuntu on 2009-04-01
getting your mic to work is a very hardware driver specific issue. Troubleshooting help is here.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by TyrantWave on 2009-04-02
Hmm... most of that is for sound issues, not recording, but following the mic input I've come to the following:

I've found out ubuntu just does not recognise my microphone jack, so it will have to be through USB.

And any time I try to test the input sound now I get the following error:
```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

Googling around about that error, all I've managed to find is that people tell you to change certain settings in the volume control, of which none of those settings are even present for me...

---

### Post by markbuntu on 2009-04-02
Many of the problems with microphones not working is due to needing to use a specific driver option for a specific sound card/chip on a specific machine due to OEM tweaking.  These issues are being fixed on a regular basis so if you were looking at months/years old posts their information may no longer be valid.


How you fix that error is to change the settings in System/preferences/sound to pulseaudio. For more on setting up your sound properly go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

For even more help you can go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by TyrantWave on 2009-04-02
I've read through those now, and followed anything that applied/
One of the guides said to enable some extra update configurations (In software sources, updates tab)

I did this, downloaded and installed about 125MB of updates, and rebooted.

Now, my Mic's *kind of* working.

It's actually getting a feed into it now (Which is good), but the feed is only static (Which is bad).

Here's what the input is:
[IMG]http://i249.photobucket.com/albums/gg231/TyrantWave/Screenshot-2-2.png[/IMG]

The volume there is actually constantly changing by a small amount (Going up & down by a few pixels, like it's vibrating).

I've tried turning the mic's volume up, but it's not letting me go higher than 93%. It just reverts back to 79% or 93% no matter what I use to edit it (Even in alsamixer, gnome-alsamixer, and the sound preferences).

My sound preferences have no options for a mic boost either =/.

Well it's some progress I guess..

---

### Post by markbuntu on 2009-04-02
Is there an autogain switch for the mic in the gnome alsa mixer?

---

### Post by TyrantWave on 2009-04-02
Yes, which is checked.

If I uncheck it I still can't change the volume =/.

---

### Post by markbuntu on 2009-04-02
The volume control issue is a bug in the alsa usb driver. It effects different devices differently on different distros. My usb headset has flaky volume control in Intrepid and jaunty but in hardy the pulseaudio volume control works correctly while the alsa vcs do not. But the mic controls work OK. There is a bunch of bug reports about this at launchpad.

---

### Post by TyrantWave on 2009-04-02
Hmm... well if all goes well I'm upgrading this laptop within a month or two (4yr old laptop..).

Best I wait till then and just use 9.04?

---

### Post by Ian Clark on 2009-04-05
I solved the mic input issue with this code.  If entering "amixer" into terminal shows capture as off, then try this:
```
amixer set 'Capture' cap
```
Minicam is still weird, but making a little progress.  I got camera working in Skype with this:
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```
as described [here]("http://wiki.mandriva.com/en/2009.0_Errata#Webcams_do_not_work_in_some_applications_.28including_Skype.29").
Audio is still broken for Ekiga, so I filed a bug report [here]("http://https://bugs.launchpad.net/ubuntu/+source/ekiga/+bug/355585").

---

