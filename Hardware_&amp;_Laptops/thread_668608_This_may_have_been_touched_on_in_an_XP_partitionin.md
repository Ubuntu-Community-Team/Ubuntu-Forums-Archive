---
title: "This may have been touched on in an XP partitioning thread but..."
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by LeoSolaris on 2008-01-15
I made a minor boo boo in the instillation of Ubuntu, and had to remove windoze (not really that bad). I took up the entire space with Ubuntu on my laptop, but now I find myself wanting to test out a few new games. I can either reinstall windows, which I am not even sure is possible without destroying Ubuntu and all of my saved material, or messing with wine. I tried Wine once and it slowed my brand new dell's boot time down quite a bit.

My question is simple... which would be easier and faster for a time constrained college student noobie Ubuntu-ist to do? Reinstall windows at the beginning of the hard drive and hope grub recognizes it again, or tinker with Wine to get the games working on Ubuntu?

I have about 24 hours on the weekend to play with this issue, and it is not really pressing at the moment, so I ask you guys.

Thanks!

---

### Post by LeoSolaris on 2008-01-20
That was strange, I wonder why I didn't receive any response at all...

I eventually re-installed windows, and had a lot of fun re installing Ubuntu to get it to work properly, after Windows removed GRUB.

It took me a few days of tweaking, and a small amount of data loss because the extra partition I set up as a data dump to swap stuff between Windows and Linux was quite big enough. (I may be new at Linux, but new to computers I am not.)

Just for future reference, is there a way to re-install GRUB without re-installing Ubuntu? I installed a GRUB version from Puppy Linux, but it couldn't load the kernel properly for some odd reason. Kept getting a kernel panic error. That was a bit out of my depth.

---

### Post by utakubeta on 2008-01-20
Hi just rad your post.
I'm sorry you never got a response, it happens.
If you are just looking to try games I would suggest one of two things before re-installing etc:
1) install a Emulator - there's 3 or so available to Linux in synaptic, install windows there

2) Get (buy) Cedega - which is a Direct X Windows emulator. it's 5 usd a month, and tey requitre you pay 3 months up front. i usually cancel and call it a 15 dollar purchase. it's good with most software/games. the downside is you only get up dates while you are subscribed. only bleeding edge games won't work on cedega, and a few that have anti-hack tools (like gunbound :( )

otherwise what you did was probably the best way to go.
reformat, make a half sized partition for windows, then install linux using the rest. you only need to make 3 partitions, a small one for /boot, a 1 gig one for [swap], and the rest for / root
the boot i think can work on 256 or less megs. it's listed somewhere.

GRUB should install automatically and self configure, leaving windows alone if you manually partition.

---

### Post by LeoSolaris on 2008-01-26
Thanks! I may try Cedega and see if it works better for me than Wine did.

---

