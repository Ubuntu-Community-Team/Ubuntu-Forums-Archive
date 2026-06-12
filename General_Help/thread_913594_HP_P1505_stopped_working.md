---
title: "HP P1505 stopped working"
date: 2008-09-07
forum: General Help
---

### Post by marsrise on 2008-09-07
I've been using an HP Laserjet P1505 printer with my Hardy install for several months without incident—it was automatically recognized on initial install and the correct driver found.  This morning it stopped working entirely.  No test pages, no printing from OO or pdf files.  The printer does work with another Linux box and an XP machine.  I'm using the P1505 Foomatic/foo2xqx driver.  It's very mysterious—I haven't done anything to the machine in the past few days except the standard updates and it was printing fine until today.  Anyone have any ideas for troubleshooting short of a clean install?  Thanks.

---

### Post by rbmorse on 2008-09-07
Is this a USB printer? 

If you run lsusb in a terminal, does the printer show up?

If not, does it show if you run sudo lsusb?

---

### Post by Sef on 2008-09-07
>  I'm using the P1505 Foomatic/foo2xqx driver

Update:  Bug in Hardy.  See this [post]("http://ubuntuforums.org/showthread.php?t=912389&page=2").

---

### Post by marsrise on 2008-09-08
> If you run lsusb in a terminal, does the printer show up?
Yes.

> Update: Bug in Hardy. See this post.
Hmmm, It looks like I'm likely SOL unless I want to install Ibex . . . 

Since my original post I even tried the semi-official, non-supported drivers found on H-P, via SourceForge, but they didn't seem to work any better.

Other suggestions are welcome, but thanks to rbmorse and sef regardless.

---

### Post by Sef on 2008-09-09
There was an update today for Intrepid Ibex, so the P1505 should run on that out of the box.  If it was applied to Hardy Heron, that should also resolve the problem.

---

### Post by marsrise on 2008-09-10
> There was an update today for Intrepid Ibex, so the P1505 should run on that out of the box. If it was applied to Hardy Heron, that should also resolve the problem.

Can an update for one Ubuntu release (Ibex) be applied to another (Heron)?  If so, how is that done?  Am I misunderstanding your suggestion?  Thanks again.

---

