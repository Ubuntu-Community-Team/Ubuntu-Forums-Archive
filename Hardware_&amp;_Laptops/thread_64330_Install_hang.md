---
title: "Install hang"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by pixiekitn on 2005-09-10
I'm trying to install Ubuntu on my IBM Thinkpad 365XD, and the screen decided to go blank in the middle of it with a blinking cursor at the bottom left.  When I ctrl+alt+deleted after watching this for several minutes, it immediately started the shutdown sequence.  On reboot, it loaded back up to the original Win95.

I didn't see any drive indicators active, was it likely still installing?  It's not easy to get it to boot to the CD, so I thought I would ask before trying again.

Thanks!

---

### Post by GreyFox503 on 2005-09-11
I googled for "365XD" and the first result was this:

[http://personal.riverusers.com/~thegrendel/laptop1.html](http://personal.riverusers.com/~thegrendel/laptop1.html)

What are your computer's specs?  If they are like that one (Pentium-120, 24MB Memory, 1GB Hard drive) then I don't know if you can install it at all.  In particular the 1GB of hard disk space doesn't seem like much.  And Gnome just won't function at 24MB of Memory I would guess.

The screen going blank during install (with no hard drive activity) is not a good thing.  If you wanted to, you could download a liveCD and try to run that to see if you can get it to run at all.

There are versions of Linux that you can get to run on older computers.  Check out distrowatch.com.  "Damn Small Linux" seems to be one of the more popular "light" distributions.

---

### Post by pixiekitn on 2005-09-11
It actually has a P 120, 40MB Ram, and a 2GB HD.  It's... difficult to get it to boot to the CD, so I've not tried the Live cd yet, but I haven't tried any other distributions yet because I LIKE the Ubuntu interface, and frankly, I'm VERY new to Linux and want one that I can start out knowing almost nothing about, and learn it as I go, without going under.   Ubuntu Live is the only one I've tried so far that seems intuitive enough for me to be able to use from the get-go.

---

### Post by GreyFox503 on 2005-09-12
I honestly never paid attention to how much disk space my initial installation took up.  To save space you could try a server installation, but that would require MUCH more work afterwards to become a usable desktop, something you know you don't want to do.  Maybe someone else knows how much you hd space you need.

That's probably enough RAM to install, but the default desktop manager is GNOME, and I doubt that would run with 40MB, so you would have to install a different one.  For future reference, XFCE is a small, quick graphical desktop that might be good for you.

Unfortunately, in the big scheme of things, it seems there are two forces here that are hard to reconcile:  you need something easy to use and install, but it has to be very minimalistic and low requirements.  Most of the so-called "newbie" distros have nice pretty desktop managers and come with LOTS of software pre-installed.  Even Ubuntu, which fits on one CD, will uncompress itself a LOT and could easily fill 2GB, not counting swap space.

Perhaps someone else knows of a distro that fits this description.

---

