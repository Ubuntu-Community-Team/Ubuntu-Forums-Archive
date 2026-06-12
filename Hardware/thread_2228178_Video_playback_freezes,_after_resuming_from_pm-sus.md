---
title: "Video playback freezes, after resuming from pm-suspend"
date: 2014-06-06
forum: Hardware
---

### Post by spiralofhope on 2014-06-06
Lubuntu 14.04, updated recently.

Steps to reproduce:

- sudo pm-suspend
- (turn on my computer)
- vlc, mplayer, etc and play any random video file.

The video on the system appears to freeze.  Audio will continue to play from the video, but I get a black screen it.

If I switch to another virtual desktop before suspending, then the system will work as expected upon resuming.  However, when I switch to the virtual desktop on which the video is playing, then the system will freeze.

After some time, I am able to drop to a tty.  Even then there are some freezing problems.  It appears that lightdm will restart after a while.

If I reboot normally, video playback works as-expected.

This does not occur with 13.04 on this hardware.

I have a GeForce GTX 650 and am using the default nouveau drivers.

I'm not sure where to begin to troubleshoot this.

---

### Post by spiralofhope on 2014-08-07
This issue is either linked to faulty memory or to poor power being supplied to my video card.

Fixing these issues, I can no longer reproduce this video playback freeze.

----

[edit]  I was wrong.

Testing on 13.04
- Originally, I was unable to reproduce this issue.
- After installing libdvdcss I was able to reproduce it.
- Even after my hardware changes, I am still able to reproduce it.

Therefore, I was wrong to suggest a power supply or memory issue.  This was a software issue resolved with some recent update.

---

### Post by maiks-github on 2014-09-23
Hey spiralofhope,

i experience exactly the same errors like you.
After resuming my system of suspend (sudo pm-suspend) and starting to play a vidoe file with vlc, the display freezes and i am only able to hear the sound.
Playing the video in tty2 works but back in graphical mode not.

I'm using not an ubuntu powered system, nevertheless i participate in this forum, because it seems that it is not an ubuntu related problem.

So my system configuration is:

Software:
fedora20 with latest kernel (3.16.2-201)
latest version of vlc (2.1.5)
i3 as the desktop environment and
and the nouveau driver

Hardware:
nvidia geforce GT 240M 4gb ram
acer aspire 7738g

maybe someone of you have an idea how do determine the error

---

