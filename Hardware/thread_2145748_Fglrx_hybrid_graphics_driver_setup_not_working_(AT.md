---
title: "Fglrx hybrid graphics driver setup not working (ATI) Need help."
date: 2013-05-16
forum: Hardware
---

### Post by Cinaed666 on 2013-05-16
Hello,

To sketch the situation: I own a Lenovo Thinkpad Edge E520 with a hybrid graphics setup (Intel integrated/Radeon). I have Xubuntu 13.04 (64bit) installed on it, 
and have recently formatted my windows partition with my favourite games coming on out on linux anyways.

What I didn't realize until trying to play Brutal Legend, was that even though I had the fglrx driver selected in the software tab, my ATI Radeon HD 6670 was not working,
and my Intel 3000 card was doing all the heavy lifting. I have tried to set up my setup many times before, and each time I've managed to break my xorg config, 
dropping me into a cli shell on startup, and startX giving me an error.

I have a lot of questions and commands that do not give me the right output, so I'm asking you kindly to walk me through it.

I have grabbed the latest catalyst drivers. Catalyst 13.3 Beta 3. Apparantly I need the beta/experimental drivers for best steam game performance.
I've also read that the latest intel drivers broke fgrlx compatibility, but I'm unsure which to replace or remove and with what version.

**My first question is:** What do I do with the intel drivers?
**My second question is:** When building the .deb packages from source with command "[COLOR=#000000][FONT=monospace]sudo sh ./amd-driver-installer-catalyst-13.3-beta3-linux-x86.x86_64.run --buildpkg Ubuntu/quantal"
WHICH build preset do I need to use, since I'm not actually on ubuntu. Is there one for xubuntu? Or do I use the 13.04 ubuntu one?

A more applicable step-by-step guide for my situation would also be very much appreciated.[/FONT][/COLOR]

---

### Post by Cinaed666 on 2013-05-17
Bump.

---

### Post by dentaku65 on 2013-05-18
I wrote a guide for the latest fglrx driver, hope it helps!
[http://ubuntuforums.org/showthread.php?t=2139200&p=12619755](http://ubuntuforums.org/showthread.php?t=2139200&p=12619755)

---

### Post by Mark Phelps on 2013-05-18
You can't just go installing drivers when you have Hybrid Graphics and expect them to work; generally, they do not.

You need to read through the material below to see if anything there helps:
[http://ubuntuforums.org/showthread.php?t=1930450]("http://ubuntuforums.org/showthread.php?t=1930450")

---

### Post by Cinaed666 on 2013-05-24
> **Mark Phelps said:**
> You can't just go installing drivers when you have Hybrid Graphics and expect them to work; generally, they do not.

You need to read through the material below to see if anything there helps:
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

This is the exact problem. I've found that thread way before, and it wants me to just install it. I do that following the obvious instructions. Download the latest ones, make them executable, build the .deb, run it, follow the install wizard and done.
It wants me to reboot, but the thread says I need to run aticonfig --initial -f first. I did that, and rebooted. No window manager.
Copying the backup of the xorg config it made over changes nothing, luckily deleting it does.

There seems to be a problem with the current intel driver, which is my question. I'm well aware how to do the actual installation and even config of the ati driver by now.

---

### Post by Cinaed666 on 2013-05-25
Bump.

---

### Post by Cinaed666 on 2013-05-27
Another bump. Anyone?

---

### Post by Cinaed666 on 2013-05-30
bump.

---

### Post by dffx on 2013-05-30
I had success using this tutorial:

[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)

I'd recommend giving it a shot. It involves downgrading a few packages that aren't precisely compatible with the Catalyst drivers.

---

### Post by Cinaed666 on 2013-05-30
> **dffx said:**
> I had success using this tutorial:

[http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)

I'd recommend giving it a shot. It involves downgrading a few packages that aren't precisely compatible with the Catalyst drivers.


Thankyou, this was what I was looking for, but I couldn't find a recent tutorial that would work.
I'll try it out tomorrow and post back.

---

### Post by Cinaed666 on 2013-05-31
Thankyou, it works very nicely. However I have noticed that in low graphics mode, docky, which I use as my default taskbar, gives me brown artifacts all over the screen?
[http://www.zimagez.com/zimage/screenshot-31-05-13-131821.php](http://www.zimagez.com/zimage/screenshot-31-05-13-131821.php)
[http://www.zimagez.com/zimage/screenshot-31-05-13-131928.php](http://www.zimagez.com/zimage/screenshot-31-05-13-131928.php)

---

