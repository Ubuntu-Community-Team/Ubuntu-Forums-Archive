---
title: "Slow CD-ROM in Jaunty"
date: 2009-05-08
forum: Hardware
---

### Post by loremonger on 2009-05-08
I finally decided to rip my CD collection, and everything went fine for about a day with a rip speed of about 20x.

The next day, doing the same thing, I can only get it up to 8x. I searched around and found this article, but it's for an older version and didn't work at all: [http://ubuntu.wordpress.com/2005/09/20/cd-rom-drive-too-slow/](http://ubuntu.wordpress.com/2005/09/20/cd-rom-drive-too-slow/)

I'm using Sound Juicer, and I'm having the same problem on my desktop and laptop. The desktop is 64-bit, the laptop is 32-bit. The CD drive reads at 20x in Windows just fine, so it's not the hardware.

Any ideas?

---

### Post by logos34 on 2009-05-08
could be a bug (either in sound-juicer [itself]("http://ubuntuforums.org/showthread.php?t=1141109") or the [gstreamer plugins]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/129383")).

You might check the cdparanoia settings, in the unlikely event something is changing them:

gconftool-2 -R /apps/sound-juicer/

> 
Paranoia mode: 0) disable 2) fragment 4) overlap 8) scratch 16) repair 255) full  

default = 8

As you probably already know, different cds/types of music rip at different speeds...some fast, some slower...maybe you just hit a batch of slower ones

just some suggestions

---

### Post by DJYoshaBYD on 2009-05-08
use RipOff.. thats what I use.. it works fast and great.. very reliable

---

### Post by logos34 on 2009-05-08
the above poster just reminded me I forgot to suggest alternative apps, which I usually do to people with sound-juicer issues. (see [this]("https://help.ubuntu.com/community/CDRipping#MP3%20Encoding"))

My advice: switch to one of the rippers listed [here]("https://help.ubuntu.com/community/CDRipping#Other%20CD%20Ripping%20Software").  They're all excellent.  A lot of people also swear by RipperX. 

I mainly use ABCDE, and Exact Audio Copy (on wine) if I want secure rips (can't get RubyRipper, which features a 2-pass rip, to work on my machine)

---

