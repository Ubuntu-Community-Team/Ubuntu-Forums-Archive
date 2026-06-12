---
title: "*sigh* Suspend/Resume on Toshiba A200"
date: 2009-10-29
forum: Hardware
---

### Post by humphreybc on 2009-10-29
Does anyone know much about suspend / resume and how to fix/troubleshoot problems with it?

If you have a look at my bug report here: [https://bugs.launchpad.net/bugs/438470](https://bugs.launchpad.net/bugs/438470)

Weird thing is that when I upgraded from Jaunty to Karmic, it started working great... but then I did a fresh install of Karmic and now it doesn't work again!!

So somehow it was working from the upgrade but not from a fresh install O.o

---

### Post by Boombino on 2009-12-08
I faced this problem on my Toshiba A200 with Mobility Radeon HD 2600 two times. First time it happened on Debian with fglrx and second - on Ubuntu Karmic with fglrx. Moreover, calling fgl_glxgears and closing it always made my system hang.

Here I must notice that clean Karmic installation didn't have these problems. Initially there were no problem with susped or fgl_glxgears. But I don't remember at which point my machine failed to wake up first time.

I performed instructions from this page:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Then I uninstalled xserver-xorg-video-ati, downloaded and installed Catalyst 9.11, and these two problems disappeared. Now my laptop correctly suspends and wakes up.

Hope, this will help.

---

### Post by humphreybc on 2009-12-08
Really? Hmm. I've tried installing the 9.10 drivers about a million times, in all the different ways and I can't for the life of me get it to boot with those drivers. That's why I'm forced to use the open source drivers and live without suspend/resume.

---

### Post by Boombino on 2009-12-09
Open source drivers worked fine for me, no problem with suspend.

Recently I've noticed that bug with fgl_glxgears returned. glxgears works without any problems. Antialiasing and texture filtering settings in Catalyst did not affect rendering, so I moved to 9.10 driver. Now Catalyst settings work, but closing fgl_glxgears still makes my laptop hang.

When my system did not wake up, I had some red pixels on the screen, always in the same place, independently on whether backfill patch was installed or whether I used Ubuntu or Debian. I saw them and mouse pointer on a black screen, mouse didn't move. Now, when laptop is waking up, this picture appears and disappears in a split second, and finally appears password dialog.

Maybe, this will give a clue.

---

