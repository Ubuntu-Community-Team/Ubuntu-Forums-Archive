---
title: "New.. everything."
date: 2005-08-30
forum: Hardware &amp; Laptops
---

### Post by lizard.boy on 2005-08-30
i was reading another forum and came across a thread explaining how somebody relaced his server with another and just transferred the harddrive.

> Get this: The entire upgrade was done with only 8 minutes and 59 seconds of downtime!

Never mind that the new system had a new NIC, a new video card, a new modem, new system buses, controllers, etc. (the things that would drive a Windows machine crazy). I renamed my /etc/sysconfig/hwconf file before shutting down, to force it to recreate it on reboot. Then I ran the shutdown command, unplugged it, and did a quick drive transplant to the new box. I lost a couple of minutes due to an unexpected prompt on the CMOS setup (unfamiliar BIOS), but was back online very quickly. Every service started up exactly like it should.

I figure I spent about 5 minutes disconnecting the machine, swapping the drive, and then connecting the new machine. About 2 more minutes fiddling with the new CMOS setup. And about 2 minutes on the reboot, going through the Kudzu prompts for the new system.  

this was done with fedora core 2, but i was wondering if something like this would be possible with ubuntu. I have a pentium 1 machine that i would like to swap with a pentium 2, without having to install everything again. thanks.

---

### Post by lizard.boy on 2005-09-09
bump.

---

### Post by kadissie on 2005-09-26
It's not an answer, but since you weren't getting any....

I came across this post when wondering what would happen if I swapped my ATI Radeon graphics card for a Nvidia card.  I couldn't find much useful - apart from someone suggesting using the kudzu package from Universe, which is the configurator in RH/Fedora - so decided to swap and see. I **didn't** use kudzu.

I made no changes before shutting down, did the swap, and then started up with fingers crossed.  X didn't start right, and dumped me into dpkg-reconfigure with ugly-looking characters all over the place.  My configuration choices didn't work right, so X once again didn't start.  I changed to runlevel 1 and ran dpkg-reconfigure again twice - failing the first time, and getting it right second time.  I can't remember what I did differently each time, but my main point is that it didn't work especially smoothly.

That said, graphics is one of the harder things to get right automagically.  So my guess is that, although not trouble-free and not to be attempted by the faint of heart, swapping an Ubuntu hard drive onto a new motherboard is likely to be doable.  More so than under Windows, anyway.

What happened with your pentium 1 to 2 conversion?

Robert

---

