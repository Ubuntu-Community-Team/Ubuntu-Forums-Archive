---
title: "problems after some ppa updates"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by Infin1ty on 2009-08-17
I don't know if it's the right place to ask but..
I have jaunty and i did some upgrades lately using launchpad ubuntu PPA, anyhow today i came across an upgrade to pulseaudio and some other stuff and i decided to try it out.
i used this one: [https://launchpad.net/~dnjl/+archive/multimedia](https://launchpad.net/~dnjl/+archive/multimedia) and ofcourse i added all the build dep, including the backports (remove the comments from the sources.list).
after the upgrade (apt-get update, apt-get upgrade, apt-get dist-upgrade) i restarted and at first the vga didn't responds (because it was set on high resolution) but then kdm started and was very very slow, later on KDE finally loaded and then i started having problems, like no keyboard at all, compiz wasn't even starting up, i couldn't do anything.
i tried to go into recovery mode and check if something went wrong, i guess something did went wrong and i saw some errors which i managed to fix.
but that didn't help, kde starts and then again, no keyboard at all, compiz won't load and the console won't use vga at all.
it looks as some package touched the kernel and screwed it up a bit because when i load it i see some errors at start regarding no block devices and grep not found like it's trying to search something and it's missing.
also it seems as the fglrx driver have some kind of error at the kernel load, i tried to reinstall it without any success removing that error.
 
i tried almost everything, my only hope is if there's someway to downgrade all those packages back to what it was before, i know removing the sources from sources.list won't help much, is there any other way? like telling it to install the basics jaunty packages instead of the new ones from that PPA? reading the "new" packages and telling it to download the basic ones instead?
 
Thanks.

---

### Post by michael37 on 2009-08-17
> **Infin1ty said:**
> I don't know if it's the right place to ask but..
I have jaunty and i did some upgrades lately using launchpad ubuntu PPA, anyhow today i came across an upgrade to pulseaudio and some other stuff and i decided to try it out.
i used this one: [https://launchpad.net/~dnjl/+archive/multimedia](https://launchpad.net/~dnjl/+archive/multimedia) and ofcourse i added all the build dep, including the backports (remove the comments from the sources.list).
after the upgrade (apt-get update, apt-get upgrade, apt-get dist-upgrade) i restarted and at first the vga didn't responds (because it was set on high resolution) but then kdm started and was very very slow, later on KDE finally loaded and then i started having problems, like no keyboard at all, compiz wasn't even starting up, i couldn't do anything.
i tried to go into recovery mode and check if something went wrong, i guess something did went wrong and i saw some errors which i managed to fix.
but that didn't help, kde starts and then again, no keyboard at all, compiz won't load and the console won't use vga at all.
it looks as some package touched the kernel and screwed it up a bit because when i load it i see some errors at start regarding no block devices and grep not found like it's trying to search something and it's missing.
also it seems as the fglrx driver have some kind of error at the kernel load, i tried to reinstall it without any success removing that error.
 
i tried almost everything, my only hope is if there's someway to downgrade all those packages back to what it was before, i know removing the sources from sources.list won't help much, is there any other way? like telling it to install the basics jaunty packages instead of the new ones from that PPA? reading the "new" packages and telling it to download the basic ones instead?
 
Thanks.

Unfortunately, the sound system in Ubuntu touches pretty much everything.  Once you upgraded pulseaudio, you didn't really damage much.  Real damage was probably done by upgrading ALSA, which is a kernel way to stream audio.

IMO I would disallow upgrading ALSA... it's usually dangerous and not very helpful.

Your best recovery option at this point might be going all the way to karmic beta.  I don't usually recommend it, but the full dist-upgrade might be able to fix it. And get rid of the PPA repositories while you upgrade.

Alternatively, you might want to ask the owner of the PPA directly.  These folks are quite helpful in troubleshooting.

---

### Post by Infin1ty on 2009-08-18
> **michael37 said:**
> Unfortunately, the sound system in Ubuntu touches pretty much everything. Once you upgraded pulseaudio, you didn't really damage much. Real damage was probably done by upgrading ALSA, which is a kernel way to stream audio.
 
IMO I would disallow upgrading ALSA... it's usually dangerous and not very helpful.
 
Your best recovery option at this point might be going all the way to karmic beta. I don't usually recommend it, but the full dist-upgrade might be able to fix it. And get rid of the PPA repositories while you upgrade.
 
Alternatively, you might want to ask the owner of the PPA directly. These folks are quite helpful in troubleshooting.
 
i was thinking alsa made it as well because it touched some configurations files, i think later this day i will go on and try to fix it myself (i emailed the owner of the PPA, hope he can help).
I do have experience with linux but not with ubuntu (i use slackware on my server) so all this apt-get is kinda new to me but i did know i could break my system down if i get the wrong package :) well anyhow, tihs is how you learn stuff...
I guess if i won't be able to fix it i will just upgrade to karmic and help with it's development (since i always find bugs :D)

---

### Post by Infin1ty on 2009-08-18
Managed to fix it myself :)
There was a big problem when compiling the kernel again, when i compiled it i was using the Intel graphic card instead of the ATI one which i use only! (i have a problem in my bios and i'm going to get my motherboard replaced, long story..) so sometimes it uses the intel and sometime the ATI, so when i recompiled the kernel it used the intel!, anyhow, i went again and recompiled the kernel with the ATI (fglrx), then removed the Intel ones completely, and it works again :) with the new pulseaudio and alsa :)
everything works smooth, also managed to upgrade my xorg server as well.

---

### Post by michael37 on 2009-08-18
fgrlx... hmm... I've had nothing but trouble with new (2.6.29+) kernels and fgrlx.  But I just noticed a few major patches that came in the past two months.  Let me know how it works.  I am using radeon driver for my ATI R500-based video card.  Radeonhd driver works too, but it's slower for 3D.  Compiz works very well.

---

