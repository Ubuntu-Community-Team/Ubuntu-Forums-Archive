---
title: "Cannot record from the mic input jack"
date: 2008-11-04
forum: Hardware
---

### Post by jonnywilko on 2008-11-04
Hi I'm currently dual-booting Ubuntu 8.04 with windows vista on a Dell XPS M1530  laptop. I recently installed a whole bunch of programs for sound recording (I believe it was the music ubuntu studio package), however I cannot seem to record through the mic input jack and every peice of software I have tried seems only able to record from the built in microphone. I know that jack works as I have successfully been able to record sound through it in Vista.

This may just be a simple configuration issue but after an hour or so of playing, I couldn't find the solution. Please help guys

---

### Post by jonnywilko on 2008-11-07
Bump.

Please help, I don't want to have to switch to vista for recording.

---

### Post by spongypants23 on 2008-12-19
I'm gonna bump this, since I'm having the same problem, although I can't get to the built-in microphones either.

Ubuntu Hardy Heron 64-bit, XPS M1530

---

### Post by BigHiGh on 2008-12-22
> **jonnywilko said:**
> . I recently installed a whole bunch of programs for sound recording (I believe it was the music ubuntu studio package), however I cannot seem to record through the mic input jack and every peice of software I have tried seems only able to record from the built in microphone. I know that jack works as I have successfully been able to record sound through it in Vista.

Same problem, both built-in mic and jack mic aren't functionning and no error reports.
Even went through this step by step guide :
[http://ubuntuforums.org/showthread.php?t=205449&highlight=Comprehensive+Sound+Problems+Solution+Guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=Comprehensive+Sound+Problems+Solution+Guide)

---

### Post by spongypants23 on 2008-12-22
**I got the Microphone Jack working. Here's how:**
Note that these instructions have only been tested on a Dell XPS M1530 with Ubuntu 8.04.1

First, I installed and configured the PulseAudio Sound Server using this How-To: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

**NOTE**: There is a chance this may cause Firefox crashes. This is caused by the flash packages in psyke83's PPA. To fix this, simply remove their repositories from sources.list, and downgrade "flashplugin-nonfree" and "nspluginwrapper" to the versions found in the Ubuntu repo. (I have my packages from hardy-backports).


_-System > Preferences > Sound_
Sound Capture is set to PulseAudio Sound Server.
All others set to Automatic.
Screenshot:
[http://i11.photobucket.com/albums/a168/spongypants23/Skrmbild-Ljudinstllningar.png](http://i11.photobucket.com/albums/a168/spongypants23/Skrmbild-Ljudinstllningar.png)


_-In the Volume Control thing_
All Input Sources are set to "Front Mic" with Digital Input Source set to "Analog Inputs".
Screenshot:
[http://i11.photobucket.com/albums/a168/spongypants23/Skrmbild-VolymkontrollHDAIntelAl-1.png](http://i11.photobucket.com/albums/a168/spongypants23/Skrmbild-VolymkontrollHDAIntelAl-1.png)


_-Open the PulseAudio Volume Control, "pavucontrol"._
Go to the tab labeled "Input Devices". Right-click on the one labeled "ALSA PCM on front:0 (STAC92xx Analog) via DMA", and tick the box labeled "Default".
Screenshot:
[http://i11.photobucket.com/albums/a168/spongypants23/IMG_0855.jpg](http://i11.photobucket.com/albums/a168/spongypants23/IMG_0855.jpg)


-Plug in your microphone. Make sure it's not muted.


-Make sure the PulseAudio Device Chooser is running, run "padevchooser" if it is not.


-Left-click on the Dev Chooser icon, and select "Volume Meter (Recording)", and speak into your microphone. The bars should move. If they do not, try adjusting the microphone/input volume.
Screenshot:
[http://i11.photobucket.com/albums/a168/spongypants23/Skrmbild-PulseAudioVolumeMeter.png](http://i11.photobucket.com/albums/a168/spongypants23/Skrmbild-PulseAudioVolumeMeter.png)




Hopefully this gets you going!
Cheers. :)

P.S. I will not be able to help you set up your favorite audio recording program. Chances are I don't know how to.

P.P.S. Don't ask me about the built-in microphones. I can't get those working. But I hear they don't work too well anyway.

---

