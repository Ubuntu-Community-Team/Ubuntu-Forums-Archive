---
title: "wont boot up"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by windy0windy on 2009-05-18
windows 98 2nd edition and ubuntu installation.  Screen comes up and asks what program I want.  Then I press Ubuntu.  After a bunch of scrolling text, I get this text:

[COLOR="#ff0000"] * An automatic file suystem check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

*The root filestystem is currently  mounted in read-only mode. A maintenance shell will now be started.  After performing system maintenance, press CONTROL-D to terminate the maintance shell and restart the system.
bash: no job control in this shell.

root@windy-desktop:"# 1[/COLOR]


[COLOR="Black"]What in the world does all that mean?  How do I get this to work.
[/COLOR]

---

### Post by Mark Phelps on 2009-05-19
> **windy0windy said:**
> What in the world does all that mean?  How do I get this to work.

What it means is that your Linux filesystem is corrupted and fails the filesystem check (fsck).

Did you install inside Windows 98 (using Wubi), or did you install in a dual-boot setup using a separate partition?

Also, how much memory does your system have?  Lots of "older" Win98 machines only had 256MB of memory and that's not enough to run the default Ubuntu desktop.

---

### Post by windy0windy on 2009-05-19
> **Mark Phelps said:**
> What it means is that your Linux filesystem is corrupted and fails the filesystem check (fsck).

Did you install inside Windows 98 (using Wubi), or did you install in a dual-boot setup using a separate partition?

Also, how much memory does your system have?  Lots of "older" Win98 machines only had 256MB of memory and that's not enough to run the default Ubuntu desktop.


My HP only has 256 MB and that is probably the problem.  I have already added all the memory the motherboard allows.  Thanks for the reply.  Rats, I really wanted to try it.

---

### Post by Rhemat on 2009-05-22
I got this error this morning too.  Here are the specs of my machine:

AMD Athlon 64 3200+ 2.0GHz
2GB DDR RAM
40GB PATA Hard Drive (Master) / 80GB PATA Hard Drive (Slave)
Ubuntu 9.04 is the only system I have installed on this computer.
I try to run fdisk, but it just fails.  It prompts for "This block is -- but it should be --", and I've tried saying yes, but it can't fix it.  I tried ignoring the error, but all I get is the bash command line.  What can I do?
Thanks in advance

==============================
As it turns out, the 40GB hard drive is corrupt.  I got a SATA one, now and it works.

---

