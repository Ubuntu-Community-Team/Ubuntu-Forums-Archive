---
title: "BadAlloc Xv errors even when &quot;Visual Effects&quot; are DISABLED"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by EXrider on 2007-11-20
I did a fresh install of Gusty on my laptop here, it's a Dell Inspiron 8000 with the SXGA+ display and 32MB ATI Rage M4 Mobility.

I'm having numerous problems with video playback. I dug around on the forums here and found others with similar problems, but theirs were all related to ATI and Intel drivers with "Visual Effects" running, so simply disabling them resolved their problem. Obviously, Compiz isn't supported on this chipset, so it's already disabled.

MythTV plays the small previews as I navigate between recorded shows, but when I play one (or live tv), I get a dark blue screen (or box depending on aspect ratio) with just sound.

Totem and VLC crash as soon as I open a video. Xine doesn't even launch without displaying a box of garbage and crashing before I can even do anything. Launching them from the terminal gives me a similar error for each one...

```
me@ubuntu:~$ vlc 

VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
me@ubuntu:~$ xine
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
AFD changed from -2 to -1
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2544
  Current serial number in output stream:  2545
me@ubuntu:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 56 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

If I config the players to not use Xv, it works, but they drop frames like crazy and use 100% CPU.

Everything had been working flawlessly in Feisty, I'm tempted to switch back now.

---

### Post by EXrider on 2007-11-26
I found my solution over[ in this thread]("http://ubuntuforums.org/showthread.php?p=3845945").

---

