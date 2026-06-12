---
title: "Boot Hangs at Checking Battery state"
date: 2008-09-11
forum: Hardware
---

### Post by jordanStone on 2008-09-11
Hey all, A first post.

Recently my mom brought home an acer 22'' widescreen LCD monitor.  In the course of trying to get my laptop (running ubuntu) to display to it, I downloaded a few installations and messed with the monitor settings in the andministration pull down thing (a lot!) .  The installations I installed I knew nothing about (i just saw them in a post about getting ubunto to work at 1680x1050).  Now my laptop won't boot! OH NO.  I can boot in recovery mode and have since removed the installations with

sudo apt-get remove (those stupid installs)

it seemed for a while that the boot was hanging at /etc/rc.local so in recovery mode I looked at rc.local and it included only 

#!bin/bash
#comments
exit 0

so I removed it, since most threads implied that ubuntu looked for init.d instead of rc.local anyways.

IN SHORT:  All I wanted to do is display to a wide-screen monitor, now I can't boot.  I toggled the screen settings a whole lot and think I may have upset the OS.  HELP!

thanks

---

### Post by jordanStone on 2008-09-11
the packages were got via:

   1. sudo apt-get update
   2. sudo apt-get install linux-restricted-modules-$(uname -r)
   3. sudo apt-get install xorg-driver-fglrx
   4. sudo aticonfig --initial

however, the aticonfig errored or didn't complete

---

### Post by tbresson on 2008-11-04
I have the same problem.

Related to the other messages here, it's probably the restricted ATI driver.

Any idea on how to disable the restricted driver without reinstalling the whole OS?

---

### Post by tbresson on 2008-11-05
I reinstalled the OS without installing the restricted driver and now everything works fine.

---

