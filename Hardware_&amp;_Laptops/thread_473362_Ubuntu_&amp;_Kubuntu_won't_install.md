---
title: "Ubuntu &amp; Kubuntu won't install"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by Syndacate on 2007-06-14
Hey,

First let me say I'm not very computer savy :(

I have a HP Pavilion 9000z and was trying to install Kubuntu, but I ran into a problem, then I dl'ed ubuntu, and the same thing happened.

The versions are 7.04 (32 bit)

The problem is that I hit "start" or "install" (the 1st option) when booting off the disk - it shows the kubuntu or ubuntu splash screen, then it starts checking stuff starting with the keymap then shows the "[ OK ]" on the other side of the screen.

It shows a list of stuff, "Ok's" most stuff - then fails at a few things - after the check it beeps and then I get a black screen - where it sits and hangs forever and ever.  Nothing works then, not even the CD eject button.  Alt+Ctrl+F1 didn't work either (no key seems to do so at this point).

I do realize that this isn't really a hell of a lot to go on but it from what I've found when looking around the web it seems to work flawlessly on this computer - so something is screwy.  Oh yeah, I did click "check CD" and it ran checks on the CD and said everything was fine (did this to both distros).

To tell what it fails at is a bit hard b/c of how fast it moves through the check list.  I did catch "hardware" and "firmware" a few times as well as "cannot open because it is damaged or not found." - though it continued with the check part - then it finishes - beeps and that's it.

I installed it (kubuntu) on my desktop (I made it, Abit IC7-G MB w/ a P4 3.0Ghz CPU, 1G corsair ram, dual sata 120g//200g drives, and a ATI Radeon 9250 - old as **** now, but was cutting edge when I put it together...irrelevant, anyways) and it works fine there, I've just been disgusted to use it b/c nobody can get the video drivers to work :( so even the 3D gears thing lags like a whore.

So if anybody's got any info about my blackscreen "hanging" problem plz, tell me, and now that I think of it, anybody who thinks they can get my vid card drivers to work on my desktop, plz tell me =P.

Thanks in advance guys, sorry for the lack of info :(

---

### Post by Syndacate on 2007-06-14
Eh, had a feeling this was one of those probs that nobody would know :(.

---

### Post by Circus-Killer on 2007-06-14
its your lucky day!

when you boot up the livecd and it brings up the bootup menu (where you can choose to load ubuntu from cd and other options). at that menu, press F6.

this will allow you to edit the kernel line. add "noapic irqpoll noirqdebug" to the startup line.
after the install, your pc will reboot, you will again need to edit that line in grub (and whenever you update your kernel).

if you have any problems or if i did not make it clear enough, feel free to ask. ;)

for more help, check this wiki page out: [https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

that wiki page is for the DV6000, but im sure some of the solutions there will help you through some of your problems.

---

### Post by Syndacate on 2007-06-14
That worked perfect, thanks, one more Q if you have the time, this one's about allocating space.

I'm tight for space on all my drives, but on my secondary 80g internal I have 31g left - so I wanna partition that out - but kubuntu seems to have a problem with that.  I didn't like any of the pre-set deals b/c I don't wanna format the whole drive, so I clicked "manual" and got this.

[IMG]http://i82.photobucket.com/albums/j271/Syndacate/Computer%20Stuff/kubuntupartition.jpg[/IMG]

I'm assuming that it's SDB but when I type in how much to partition (25000) it won't let me).  In that box there it starts off with 80000, then when I go to replace that with 25000 or 20000 it won't let me, as you can see, it only allows 2000mb ~2g.

None of the auto features work b/c I don't have 44g left.  I know it would be better & easier to do this on a hard drive that had more room and/or new drive but right now I'm trying to press it out of this.  I'm thinking about using partition magic and creating a partition on the D:\ (SDB) drive but I've had bad experiences with partition magic.  On my PC I partitioned with kubuntu - but I had a lot more room (120 gig empty HD since it had a melt down) to work with so it went smooth.

Thanks already for your help, and TIA.  I seriously did not think anybody would know what the hell happened - black screens w/o error logs usually suck - but I guess what u did made sense..thx

---

### Post by Circus-Killer on 2007-06-14
i'm sorry, but i have no idea on your partitioning problem. i have never bothered to resize a partition. what i suggest is for you to start a new thread titled "help with resizing partition" or something like that, you'll get a response quick, its a popular topic.

also try search the forum for "resize partition" and see what results come up. i can garuntee that you are not the first person on this forum thats had this resizing partition problem.

anyways, sorry i couldnt help you further. best of luck. :D
cheers.

---

