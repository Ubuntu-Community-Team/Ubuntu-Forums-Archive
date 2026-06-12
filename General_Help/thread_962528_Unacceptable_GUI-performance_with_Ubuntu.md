---
title: "Unacceptable GUI-performance with Ubuntu"
date: 2008-10-29
forum: General Help
---

### Post by GRK on 2008-10-29
Hi everyone,

I'm using Ubuntu for about 3 weeks. After the startup everything works just fine (fluent GUI, everything fast, 3000kbps INet, ...). 

But recently it tends to have **terrible **performance most of the time once I use basic programs like firefox with 3-5 tabs and 1 download, Rhythmn box music player, pidgin and sometimes netbeans. I mean really terrible: Slllooowwww GUI, 2-3 fps mousepointer, characters I type appear 1 second later, INet speed goes down to 200kbps and the music player is bucking all the time. Even when I close down there is no chance to do anything under those conditions. It feels like using a Pentium 1.

This is unacceptable, because I never noticed a single performance flaw under WinXP for half a year (actually it runs fluently as a waterfall) with my decent hardware setup: *Intel C2D 4600, Asus P5B-VM, GeForce 8800 GT, 4GB DDR2 Ram, Asus WLan Stick*
I use the best available linux driver for that Gfx-Card (which unfortunatelly still sucks ..)
Even my 5 year old laptop with WinXP runs the described apps 5 times more fluently than my kinda new ubuntu-machine

The weird thing is that I can't explain this with common sense (I'm not a computer-newbie, only new to linux) and I see no reason for this behaviour in the system monitor. When the whole GUI and I/O is almost frozen, the system monitor shows no process with more than 5% CPU usage and the graphs for the 2 CPU cores oscillate somewhere between 20% and 60%. 
It appears to me that downloading a file and the firefox flash plugin are the biggest bottlenecks.

I'd be glad if someone could provide a solution or at least explain the behaviour :)
I know I can't blame only Ubuntu because the proprietary flash- and nvidia-support for linux sucks ... but I have to say that I'll most likely abandon ubuntu as an operating system for everyday's use if there is no possibility to use the most basic multimedia apps fluently on my quite new machine. But since this issue wasn't always present, I hope there is a solution =)

---

### Post by Don S on 2008-10-29
Have you tried disabling Compiz, and see if it still reacts the same way? Some users have problems with Compiz and graphical performance.

```
metacity --replace
```
To disable Compiz.
```
compiz --replace
```
To enable Compiz.

---

### Post by mkvnmtr on 2008-10-29
Also check how full your hard disk is. One time, I think it was on 6.06 the logs were not deleting and my disk filled up and that gave me similar problems.

---

### Post by GRK on 2008-10-29
> **mkvnmtr said:**
> Also check how full your hard disk is. One time, I think it was on 6.06 the logs were not deleting and my disk filled up and that gave me similar problems.
Good idea, but all relevant partitions are filled 36% or less.

> **Don S said:**
> Have you tried disabling Compiz, and see if it still reacts the same way? Some users have problems with Compiz and graphical performance.

```
metacity --replace
```
To disable Compiz.
```
compiz --replace
```
To enable Compiz.
ok, I'll try that now. I've already disabled all desktop effects though because they caused problems while using java window apps (like netbeans).

thanks for the input 

BTW:
It's odd that after a fresh startup, everthing runs oh so smooth but after the first troubles occur, the smooth status can't really be obtained again. Maybe some service with heavy interrupting and I/O is running then? Seems so ...

EDIT:
omg, also having WLan problems now ... back at WinXP for the moment

---

