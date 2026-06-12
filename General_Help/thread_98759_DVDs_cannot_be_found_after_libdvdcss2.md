---
title: "DVDs cannot be found after libdvdcss2"
date: 2005-12-04
forum: General Help
---

### Post by Drunken Pirate on 2005-12-04
I installed libdvdcss2 from deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main, and everything went OK. But now when I try to play a dvd it says it cannot be found. (MPLAYER: failed to opem dvd://1) and a similar error in totem. If I remove libdvdcss2, it just freezes up when I try to play. I am able to play DVD's that don't have any CSS protection, so I know it has somthing to do with libdvdcss2. Any suggestions?

Heres the mplayer error:>  mplayer dvd://1
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 0)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for Debian.


86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
Couldn't open DVD device: /dev/dvd
File not found: '1'
Failed to open dvd://1


Exiting... (End of file)


My dvd device is /dev/hda
/dev/dvd exists

---

### Post by AmphetaMarinE on 2005-12-04
i too receive this same error, only on playback of dvd's which are css encrypted...

---

### Post by Drunken Pirate on 2005-12-04
Yea, same thing. I can play my backed up dvds that I copied and decrypted in windows, but If I go to blockbuster and pick up a DVD I cannot play it.

---

### Post by Jengu on 2005-12-04
After you install libdvdcss2, close the player, eject the dvd and reinsert it, then restart the player. For some reason that seems to be required. Also try with totem-xine instead of totem-gstreamer.

---

### Post by Drunken Pirate on 2005-12-04
Thanks, that worked. I feel like a idiot!;)

---

### Post by AmphetaMarinE on 2005-12-05
I second that Drunken Pirate...
/me slaps his forhead...

Thanks a bunch Jengu... now EVERY SINGLE thing works perfect for me under breezy :)

---

