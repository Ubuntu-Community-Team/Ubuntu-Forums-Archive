---
title: "Asus M70 horrible beep on every other boot."
date: 2008-09-16
forum: Hardware
---

### Post by t.rei on 2008-09-16
Hi,

Hopefully someone around here can help me out.  I have this strange VERY LOUD beep on every other... maybe 1 out of 3... boots of my ubuntu (8.04 and intrepid showing the same behavior). It starts out as several very fast beeps and continues for about 30-60 seconds until at some time it stops and the normal boot continues.

I have muted the speakers in the BIOS and turned of the boot chime, since I often reboot at work and this is getting really really bad.

I got everything else - at least everything I need - working fine now: speakers, audio-jack, video (although performance is still a tad low). Just this really really bad sound that makes me scared of booting ubuntu because my neighbors just might call the firefighters. ;)

I am running this:
**Asus M70-Serie Modell M70VM-7U047C**
CPU: T9400 (2x 2.53 GHz • 6MB 2nd Level Cache • 1066 MHz FSB)
Screen: 17" LCD WUXGA (1920 x 1200 Bildpunkte)
Graphics: nVidia® GeForce™ 9600M GS
Sound: 24 bit Intel® High Definition

Dual Boot:
Vista
Ubuntu

Thanks to all you helpers. :)

---

### Post by t.rei on 2008-09-16
I am now following a hin I found after googling for ages:

Disabeling usplash via "startupmanager". (*apt-get install startupmanager* )

Unfortunately my neighbours will certainly kill me if I try that this evening (its way past bedtime).

---

### Post by t.rei on 2008-09-20
Just wanted to let you guys know, that disabling the usplash was a fast and easy solution to the problem.

---

### Post by squee on 2008-10-08
Thanks for that. I really needed that solution. Hope it helps!

---

### Post by tvtech on 2008-11-01
I have an asus m70vm-c1  with the same error, the other two problems come up as well, there is no way to regulate the light sensor on install and the backlight does not turn on after suspend although the monitor does recover it's just so dark you cant use/ see it. 

I've filed a bug report on launchpad about the beep.  if you want to add your boot logs and let me know where to grab mine so we can perhaps figure out what is happening that would be great. 

[https://bugs.launchpad.net/ubuntu/+bug/292121](https://bugs.launchpad.net/ubuntu/+bug/292121)

---

### Post by t.rei on 2008-11-03
Actually since the release I have turned the splash back on (use this @ work and since I want to promote the use of opensource and linux it needs to look sharp *sigh* bosses ;) ) and have not hat the beep error for a couple of days now.

---

### Post by tvtech on 2008-11-04
Are you still running this as a dual boot install? 

my current configuration is dual boot, with windows vista home premium on my primary master HD  and ubuntu on my secondary hardrive,  I had the horrible beep every other boot or so, but boot logging has been disabled in 8.10  because of problems with a library from what I've read.   so i haven't had luck getting it re-enabled, I disabled usplash  on boot and now every other boot I boot to black screen,  I am currently using the nvidia proprietary driver 177,  which may be the problem, I haven't looked at my xorg file yet, that's my next stop.   I also have a problem with suspend where it doesn't turn the backlight for the lcd on, I also have a problem with the ambient light sensor as it is disabled.   and i cannot adjust the brightness of my screen.   this may be a problem with the nvidia driver but I haven't had time to check.   let me know your config maybe it's a driver issue on my end and I can do more testing.

---

### Post by Gilles.t on 2008-11-09
Same beep on boot on my asus M50VM with 8.10.
I removed splash from /boot/grub/menu.lst to avoid this since alpha 6.
I've tried to turn splash back after some kernel updates, but problem not yet solved for me.
So, I removed splash once more...

---

### Post by tvtech on 2008-11-09
I haven't found a solution to put this back but I did find a bug report on launchpad [bug # 255590]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255590")

I think this may be related the a bug I filed where my hardrive locks out and won't mount after Grub.  Still trying to sort that one out though.

I've noticed that there seem to be a host of related issues, on both the M70 and M50, any chance that your LCD backlight does not re-initialize after suspend?  and check out this link of problems that some one else started, I just added mine to it. [COLOR="Lime"]http://ubuntuforums.org/showthread.php?t=973742[/COLOR]

I specifically waited for 8.10 to come out since most of my hardware wasn't supported until kernal 2.6.27 and more specifically was not supported under 2.6.24

---

