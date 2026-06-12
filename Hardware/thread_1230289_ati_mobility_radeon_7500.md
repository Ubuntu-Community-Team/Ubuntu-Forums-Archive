---
title: "ati mobility radeon 7500"
date: 2009-08-03
forum: Hardware
---

### Post by -Max on 2009-08-03
Hi everyone!

I've tried to get 3d acceleration for my mobility radeon 7500, 32 MB, running on a T41-thinkpad. On Suse Linux 11.1 I changed the driver in yast and it works fine - so it must be possible to get acceleration for my graphics card.

The problem on ubuntu 9.04
a proprietary driver - the catalyst - does not work with the card - it starts at radeon 9500.
                [B]fglrx doesnt seem to work as well... I've installed the packages (fglrx-kernel source and xorg-driver-fglrx + dependencies) in synaptic and after I deleted the standard radeon driver I got severe graphics problems and had to reinstall the system (i know that was stupid...).

[B]My ubuntu - I've installed it a couple of days ago - works very well and therefore I don't wanna use another distribution. Unfortunately I'm not even able to watch dvd's or videos without a faster graphics card...

What driver am I suppesed to use? And where can I find an installation guide?

Regards and thanks
Max

PS I've found and worked with a couple of installation guides and with those installed the catalyst and fglrx - but both don't seem to be right for my graphics card...
[/B][/B]

---

### Post by -Max on 2009-08-03
PS: 

I've searched on the forum and tried the following:
[http://ubuntuforums.org/showthread.php?t=1147352&highlight=radeon+7500](http://ubuntuforums.org/showthread.php?t=1147352&highlight=radeon+7500)

But it just improves my 2d performance. 
Unfortunately the card is as slow as before on videos.
Do I need 3d acceleration in order to watch videos?

---

### Post by arnold15 on 2009-09-06
My Radeon Mobility 7500 works disastrous! Its very slow when i am surfing the net.. How to accelarate it? Teach me.. Thanks!

---

### Post by overdrank on 2009-09-06
> **arnold15 said:**
> My Radeon Mobility 7500 works disastrous! Its very slow when i am surfing the net.. How to accelarate it? Teach me.. Thanks!

Hi and I have a ati 7500 with Jaunty 9.04 and it works well with desktop effects and videos. The driver that comes with the install works good. Have you tried using the xfix option when booting into recovery mode?

---

### Post by NoXiS on 2009-09-07
Firstly the closed source driver (fglrx/catalyst - same thing?) is NOT the correct driver for the Mobility Radeon 7500. You want to be using the open source 'radeon' driver.

I have this GPU in my laptop and using this driver I get acceptable performance for running compiz (although it still isn't great for full-screen video).

Xorg does tend to work quite well without an xorg.conf file these days and if I was you I would try running x without an xorg.conf file and see how it goes (don't just delete it - rename it)

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.07092009
```

If it all goes horribly wrong just make sure you know how to rename it back again outside of X. i.e. Switch to a different virtual terminal (Alt+F1 or Ctrl+Alt+F1 if you happen to have X running) and login. Rename the file back to /etc/X11/xorg.conf and you will be back to where you started.

This may or may not work, but there is a high probability that it will, and is definitely the easiest way to fix it. Besides all the cool kids are running without an xorg.conf file these days ;-)

---

