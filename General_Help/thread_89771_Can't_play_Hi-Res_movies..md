---
title: "Can't play Hi-Res movies."
date: 2005-11-13
forum: General Help
---

### Post by xsmind on 2005-11-13
Hi, I have some weird problem. When I try to play some hi-res movie. HDTV 1280x720 for instance I can't. I've tried VLC and Totem, and they both quit fast. Running from terminal gives this:
```
(totem:11266): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:11266): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 85 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

and this with VLC:
```
VLC media player 0.8.2 Janus
[00000289] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  73
  Current serial number in output stream:  74

```
I've tried newer version of VLC(which is default in breezy) and it gives the same error.

I am sure, my machine is capable of playing hdtv's, because the computer came with XP Home and VLC is playing these movies fine. Anyway the computer is FS Amilo L1300, Celeron M 1.3, 512 RAM, i855 video, 40Gb HDD and 1280x800 display res.

---

### Post by zevs on 2006-01-19
as i was searching this forum but didn't find an answer to this problem i'm bumping this thread instead of making a new one.
I've just installed ubuntu 5.10 on my laptop, and just as xsmind (please let me know if you got this working man) i'm having big problems running HDTV streams on my laptop. All my media players crashes when i try to playback hdtv streams.
both 720 progressive and 1080 interlaced video streams crash my players. for example vlc gives me this output:

```

VLC media player 0.8.4-svn20040920 Janus
[00000313] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:384000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
Xlib: unexpected async reply (sequence 0x2097)!

```

i've also tried to change video out device in Mplayer, x11 and opengl. these will play the video, but very slow, about 2fps maybe. Mplayer also gives me a message saying my system is too slow, but thats bullshit ;)
I recently had an installation with Fedora Core 4 and hdtv streams played silk smooth in all media players.
i may add that all other video formats plays just fine

anyone know what can cause this problem?

thanks.

---

### Post by deadite66 on 2006-08-13
i'm having the same problem to :<

---

### Post by Mark Conrad on 2007-07-31
Same problem, Ubuntu's Feisty Totem movie player can't play Hi-Res videos.  The movie player just blinks off and is gone.

Mark
New Jersey

---

### Post by deadite66 on 2007-07-31
i found out my problem was the onboard graphics card didn't have enough memory to display them, bought i nvidia card with 128MB memory and HD videos play fine.

---

### Post by ramjet_1953 on 2007-08-01
This problem is usually because of a lack of RAM for integrated video chipsets.

This may help:

Open your [COLOR="Blue"]/etc/X11/xorg.conf[/COLOR] file in Super User Mode

Add these two lines under the [COLOR="Blue"]devices[/COLOR] section

[COLOR="Red"]Option "VideoRam" "65536"
Option "CacheLines" "1980"[/COLOR]

Regards,
Roger :cool:

---

### Post by shirilover on 2007-08-01
If the Hi-Res movies you are talking about use the H.264 encoding algorithm, then you will need sufficient processing power to play them (at least 2 GHz, dual-core is preferable).

The amount of RAM and your video card will have little effect on such video streams.

---

### Post by zevs on 2007-08-02
I recently found the solution to this problem. It has nothing to do with the codec used, but the actual video resolution. I posted in another thread how to fix this, you can find it [here]("http://ubuntuforums.org/showthread.php?p=2366058#post2366058") (no need to double post, the last reply by me on the bottom of the page) hope that helps

---

