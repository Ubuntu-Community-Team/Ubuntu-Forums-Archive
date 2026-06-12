---
title: "Electricsheep Zooming problem"
date: 2005-11-20
forum: General Help
---

### Post by plueken on 2005-11-20
I installed Electric Sheep, ran in for a while so it downloaded and started displaying sheep, so everything is working fine.  However, if I set the screensaver to Zoom to fullscreen, it simply moves it to the upper left of the screen in the same regular resolution.

I tested it by running it from the command line with --zoom 1, and it gives the error "warning: cannot zoom without mplayer or rootwin."  I don't know what rootwin is, but I do have mplayer installed (or at least many mplayer parts, such as mplayer-586, mozilla-mplayer plugin, etc.)

Does anybody know what I need to do to get it zooming correctly?  Thanks.

- Plueken

---

### Post by Angry penguin on 2006-02-25
I am having the same problem with electric sheep only being displayed in the upper left corner of the screen. What gives? anybody?

---

### Post by underwater on 2006-03-26
Same problem here.  Won't do fullscreen.  I have no idea why

---

### Post by th3gh05t on 2006-07-07
I am also having these problems with the Sheep.

I sent in an e-mail one of the guys over @ Sheep, and he told me this command:

"mplayer -vo xv -fs ~/.sheep/*.mpg"

This made the screensaver go into fullscreen, but I don't know how to make it stay like that.

Anyone help us out here?

---

### Post by xolot1 on 2006-07-23
you could find the electricsheep executable (i think its /usr/bin/electricsheep),
rename it electricsheep.original (in case you want to revert back)
and in its place make the file electricsheep
```

#! /bin/bash
mplayer -vo xv -fs ~/.sheep/*.mpg

```
then make that file executable.

this method would allow playing of the sheep, but i dont think it works to generate more.



related question, when i use this method, my clips are only about 5 seconds long. is this because only a fraction of the sheep has been downloaded?
i get this error message as well:

```
willi@willi-laptop:~/.sheep$ mplayer -vf spp -fs ~/.sheep/*.mpg
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer; Athlon 64 X2 Toledo; Turion Newark,Lancaster (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing /home/willi/.sheep/00202=18140=18140=18140.mpg.
VIDEO:  MPEG2  640x480  (aspect 2)  30.000 fps  9000.0 kbps (1125.0 kbyte/s)Opening video filter: [spp]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 640 x 480 (preferred colorspace: Mpeg PES)
[PP] Using external postprocessing filter, max q = 6.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12  [fs]
V:   4.3 128/128 18% 154%  0.0% 0 0
Playing /home/willi/.sheep/00202=18208=18208=18208.mpg.
VIDEO:  MPEG2  640x480  (aspect 2)  30.000 fps  9000.0 kbps (1125.0 kbyte/s)Opening video filter: [spp]
==========================================================================

Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
[PP] Using external postprocessing filter, max q = 6.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12  [fs]
V:   1.1  32/ 32 18% 119%  0.0% 0 0

```

---

### Post by Pyr3 on 2006-07-24
Had/have the same problem.

Try this:


If you have replaced gnome-screensaver with xscreensaver, run xscreensaver-demo.

Then choose _M_ode: _O_nly one screensaver.

Highlight Electric Sheep.  Then click settings.  Enable zoom.

The click the up arrown under the list.  Click to exit the Drift screensaver.  Click the down button.  Electric Sheep should be fullscreen. Click to screensaver. Close Xscreensaver.

Works for me.

Odd bug, but that's how i got it to work.

---

### Post by TrinitronX on 2007-02-10
I'm getting this too, running it with the options: 
```
electricsheep --zoom 1 --root 1
``` gets rid of the "warning: cannot zoom without mplayer or rootwin." error, however, I see another error: "Cannot find xv port"

---

### Post by spin2cool on 2007-02-10
I'm told that this patch will sove the problem:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1640631&group_id=68853&atid=522601](http://sourceforge.net/tracker/index.php?func=detail&aid=1640631&group_id=68853&atid=522601)

I'm having trouble getting electric sheep to compile, though - with or without the patch.

I keep getting the error:
```
video_out_x11.c: In function &#8216;overlay_draw&#8217;:
video_out_x11.c:413: error: &#8216;x11_frame_t&#8217; has no member named &#8216;xvimage&#8217;
```

---

### Post by bob31984 on 2008-03-29
> **xolot1 said:**
> 
related question, when i use this method, my clips are only about 5 seconds long. is this because only a fraction of the sheep has been downloaded?


No, all sheep are about 5 seconds long. electricsheep knows the order they should be played in so that each sheep runs seamlessly into the next.

---

### Post by neutro on 2008-05-15
I know I'm very late in this thread (my excuse being that I didn't knew about electricsheep until yesterday), but for all of you not able to run in fullscreen, just run ```
electricsheep --zoom 1 --mplayer 1
```. According to the man page, by default, electricsheep uses its own built-in mpeg player. The --mplayer 1 option tells it to use mplayer instead, which is the only player supported with the --zoom option. Once you do that, you can use standard mplayer commands (such as F to toggle fullscreen mode). Nice to know for parties.

---

### Post by Gourgi on 2008-05-17
> **neutro said:**
> I know I'm very late in this thread (my excuse being that I didn't knew about electricsheep until yesterday), but for all of you not able to run in fullscreen, just run ```
electricsheep --zoom 1 --mplayer 1
```. According to the man page, by default, electricsheep uses its own built-in mpeg player. The --mplayer 1 option tells it to use mplayer instead, which is the only player supported with the --zoom option. Once you do that, you can use standard mplayer commands (such as F to toggle fullscreen mode). Nice to know for parties.

```
dimitra@igna:~$ electricsheep --zoom 1 --mplayer 1
Terminated

```
:(
still not working here
electric sheep keeps displaying at top left corner of my screen despite choosing xscreensaver or gnome-screensaver

---

