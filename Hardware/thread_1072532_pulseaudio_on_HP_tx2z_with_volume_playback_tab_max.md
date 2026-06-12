---
title: "pulseaudio on HP tx2z with volume playback tab max to 0db"
date: 2009-02-17
forum: Hardware
---

### Post by Vincent_Lin on 2009-02-17
Hi,

I have this HP tx2z installed with ubuntustudio 8.10 64bit.

I have tried many ways of installation but the sound simply would not come out at all. I found out that pulseaudio configuration screens have this funny stuff.

When I am running vlc to play an mp4 files, say Cars, ripped by HandBrake.

1. vlc is still playing video, but no sound.
2. Default Server - Default
-   Default sink - Default
-   Default source - Default

-   Volume Control
-         Playback tab shows vlc is playing: audio stream
-                      But Front Left max to 0 dB
-                          Front Right max to 0 dB

-         Output tab shoud ALSA PCM front:0 (ALC268 analog)via DMA
-                          Front Left has max 100%
-                          Front Right has max 100%

-         Input Devices tab show ALSA PCM on front:0 (ALC268 Analog) via DMA
-                          Front Lext has max to 100% but is at 87%
-                          Front Right has max to 100% but is at 87%

-   Volume Meter (playback) showing signal levels for ALSA PCM on fornt:0 (ALC268 Analog) via DMA, with two constantly moving bars for both Front Left and Front Right.  These moving bars show me that the audio/sound output is really going into pulseaudio server, but my playback tab in Volume Control has max volume set at 0.00dB.

The Main Volume Control on gnome panel shows max volume, and Device is set to HDA ATI SB (Alsa mixer) with all main, headphone, PCM, front cranked up to max.

My questions are: Is this Playback tab showing 0dB max on both Front Left and Front Right the reason that causes no sound on my computer?  If so, how can I set them to some sensible values?  And is there a configuration file that I can set some values for them?

Are there any other places I should look into?

Thanks for the help.

Vincent Lin

---

### Post by Vincent_Lin on 2009-02-21
Hi,

I am responding to myself and trying to document what I have done.

I have tried:

1. installed ubuntustudio-64bit with, and without all those media-production specific programs.

2. I have tried all the model= options as documented in ALSA-Configuration.txt came with my version of ALSA.  

3. With the minimum installation (without media-production programs), sound works.  I can also adjust sound volume from gnome panel's Volume Control, as well as tx2z's physical buttons.

4. With the installation of fglrx and wacom driver, sound is still there (I am using model=3stack), where direct-rendering and rotation(xrandr), stylus, touch, all work.

5. But after I installed tuxpaint, the sound started to behavior strange.  That's the program I really want to install for my girls to draw on the screen using stylus and touch.  Inkscape is another I installed, to take advantage of the touch sensitive applications.  Sound screwed up afterwards.

6. So I looked it up what was installed with tuxpaing and libsdl came out.  Then I searched libsdl and pulseaudio.  

Man!  What a mess.  

libsdl and pulseaudio do not work in a universal and straightforward way.  There are many documents about libsdl-alsa, libsdl-pulse, and libsdl-all stuff and basically, for libsdl, alsa and pulseaudio are mutually exclusive.

I will study more to find out the solution to what I need.  Ultimately, a scenario for these components to work together:

AMD 64bits /w media production programs (ubuntustudio 64)
gnome
alsa
pulse
libsdl

If anyone has a definitely solution, I am all ears.

Cheers,

Vincent

---

### Post by markbuntu on 2009-02-21
try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If that does not help, you need to go here ( I just updated it, it is almost entirely rewritten and has a lot more basic troubleshooting help)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Vincent_Lin on 2009-02-21
Thanks.  

I am reading these two threads now.

Will post the result.

Vincent

---

