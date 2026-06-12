---
title: "ubuntu:ubuntu not - how much space?"
date: 2005-01-24
forum: Installation &amp; Upgrades
---

### Post by sharkzf6 on 2005-01-24
I tried installing ubuntu on an old 2 GB hard drive I use to have Debian Woody installed on. The thing couldn't do a full install on that little 2 GB hard drive because there wasn't enough room?! Heck, I've had 2 versions of Debian on that little drive with KDE and Gnome along with full versions of Open Office.org, Mozilla, T-Bird, games, all kinds of stuff....talk about bloated! Might as well be loading WinBlows. Color me unimpressed....I'm sticking to Debian.

 [-(

---

### Post by barbarian on 2005-01-24
Today I was trying to install **custom**  ubuntu on 2.1 GB HD, also without succsess.. I was trying Warty and Hoary both.. Warty has stack on installing base system; output sad that I needed gnupg and grep installed before above mentioned step.. 
Hoary has nearly installed but on the final step appeared notification about broken X-server.
But I'm not givin' up, I'm planning to try with Debian or probably DamnSmallLinux.. :D

---

### Post by az on 2005-01-24
Shark - Use the custom install. or better still,

boot the installer with 'linux archive-copier/copy=false'


You only need about 1.6 gigs for that.


Barbarian - Sounds like your Warty cd is borked.  Try buning at a slower speed.

---

### Post by barbarian on 2005-01-25
Thanx, 
I think one more reason: HD maybe damaged because in both cases I've got strange message on the hardware detecting step, something like "input/output error" I think maybe 1,2 sectors broken closer to end of the disc. Maybe I need custom partition, to keep out boot part from damaged sectors. Btw e2fsck utylity stack also..
I'm gonna read about partitioning more.. Also maybe somebody knows more diagnostic utilities under linux to check out HD?

About system:
Pentium 200MMX proc.
Memory:160MB ram
Video: Ati Mach64VT 2MB
Seageate HD 2.1 GB

---

### Post by J. S. Jackson on 2005-01-25
[QUOTE=sharkzf6]

I tried installing ubuntu on an old 2 GB hard drive  [snip]

...talk about bloated! [snip][/QUOTE]

Well gee.  I don't think that's bloated by any sensible modern standard.  Rather better to say that your HDD is ANCIENT.  Occasionally, every decade or so, you could maybe update your HDD?   :mrgreen: 

An 80 gig drive, 7200rpm with 8mb cache can be had for $69 at newegg!

---

### Post by barbarian on 2005-01-25
Thanx, I know how to spend $69  :D

p.s. I have already new system, just playing with some ancient hardware..

---

### Post by sharkzf6 on 2005-01-25
I must apologize deeply. I installed the thing again without letting it go to the net to retrieve updates and it worked flawlessly! Everything works! After a week with Debian Woody I never even got close to this. I'm truely amazed.

> [b]Well gee. I don't think that's bloated by any sensible modern standard. Rather better to say that your HDD is ANCIENT. Occasionally, every decade or so, you could maybe update your HDD?

An 80 gig drive, 7200rpm with 8mb cache can be had for $69 at newegg![/b]

LOL, I realize this. I have a Winblows gaming rig I built myself that has all the high end goodies...can you say Counter Strike Source sessions in excess of 6 hours without so much as a hicup! Thank you nVidia GeForce 6800. The point was, it didn't install correctly the first time and I've always looked at Linux as being the light-weight operating system. I'll never replace my gaming rig for obvious hardware/gaming issues in Linux (Audigy still has no support AFAIK), however, I think I'll build a dual-boot system and use this as my primary operating system for daily tasks...re-color me...*very impressed*  :-D

---

### Post by barbarian on 2005-01-26
Thanx for replies, HD was fysically damaged. I have downloaded [SETOOLD.ISO](http://www.seagate.com/support/seatools/) (diagnostic utility for seagate discs). The first test showed more then hundred bad blocks with the mark-40h(unrecoverable error).  It's time to prepare my $69 :-P

---

