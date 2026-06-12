---
title: "Suspend/Hibernate Issues Toshiba Satellite L305D"
date: 2008-12-23
forum: Hardware
---

### Post by johnnyp14 on 2008-12-23
I've got a swap with plenty of room for suspend/hibernate, but cannot properly resume from either. Black screen with no keyboard, touchpad, etc. working. Same story as many. Hard reboot is only *solution.

Been searching the forums for a month now and tried many of the posts' suggestions but to no avail. Any help with this problem is MUCH appreciated. I dual boot with Vista, but the less I use MS the better. Here are the specs:

Toshiba Satellite L305D-S5895
Ubuntu 8.10 (fresh install)
AMD Turion(tm) 64 X2 Mobile Technology TL-60
3GB 667mhz RAM
250GB HD
ATI RS690M Radeon X1200 Series

fdisk -l:
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         191     1534176   27  Unknown
/dev/sda2   *         192        7840    61440592+   7  HPFS/NTFS
/dev/sda3           29358       30401     8385930   82  Linux swap / Solaris
/dev/sda4            7841       29357   172835302+  83  Linux


I'm relatively new to Ubuntu, so please take it easy =)

Any suggestions or extra info let me know and I'll try my best. Thanks again and Happy Holidays to all!

---

### Post by johnnyp14 on 2008-12-24
bump

---

### Post by johnnyp14 on 2008-12-25
bumpin again

---

### Post by neilobremski on 2008-12-28
I have the exact same issue with my Toshiba M15-S405 laptop ... and I am also very noobish.  Let me know if there's something I can run to provide a dump of relevant information to this problem.

---

### Post by user_ex on 2008-12-29
I have the same issue. Has anyone found a solution for this yet?

---

### Post by johnnyp14 on 2009-01-10
bump please for help

---

### Post by rahaman.naik on 2009-01-22
I too have the same issue with my Lenovo Y 500. Pls help out.

---

### Post by satellite8.10ITM on 2009-01-28
Also have this issue. Several variances however:

Satellite A215-S7437
AMD64X2 Turion
2GB RAM
100GB HD
ATI Radeon X1200 series
Ubuntu is installed using Wubi atm (does anyone else with this issue use Wubi too?)

Suspend and Hibernate both result in the same symptoms; A blinking command prompt underscore on a black screen. hard drive light blinks like suspend/hibernate would produce, but after it stops, the power light remains blue instead of changing to the slow fade orange that indicates suspension or hibernation state and the screen continues doing the same thing.

Anyone with a more thorough knowledge of what's going on here than me please help =)

thanks

---

### Post by johnnyp14 on 2009-02-06
yet another bump to get the attention of anyone..plz

---

### Post by lvleph on 2009-03-12
I guess I will bump this too. I doubt we will find a solution, but...

---

### Post by davidmohammed on 2009-03-14
... this may or may not help - I've got a Toshiba Satellite Pro A30.  I had similar issues.  The solution was to deinstall the default network manager and install wicd instead.

Hope that helps.

---

### Post by aux_anges on 2009-07-08
I've got something similar with my Toshiba Satellite L30. After it's hibernated and I want to power it up, the lights and ventilator switch on and it behaves as if it were trying to boot over and over again, but it's unsuccessful, so I have to restart it manually :(
 
Also, I've got a dual boot with Windows XP, Ubu is the one that loads automatically but sometimes it doesn't load and I've only got a black screen. I think this might be related to the hibernate problem :(
 
Any ideas what's going on with it?

---

### Post by daemon3 on 2009-08-17
Bump, too.
Toshiba L305
Thankfully I get output when my system freezes, so I know it's a kernel panic.  I tried recompiling my kernel, but that just made my system slower and more buggy.
I also get a kernel panic when I switch users.  Thankfully, on the latest upgrade, Ubuntu stops me from crashing the system, but it's still a nuicance to have a single-user system.
Hopefully with Keramic we'll get better Toshiba support. :)

---

### Post by thenailedone on 2009-08-18
... seems pointless to just add to a thread which has been around so long and received so little assistance :confused:

Well I also have a Toshiba Satellite L300 (something or other) and I can forget about hibernate or sleep... screen goes blank... and thats how it stays until hard reboot... (using Ubuntu 9.04 btw)


Cheers
Neil

---

### Post by oldrocker99 on 2009-08-20
I wish I could help. I am running Intrepid (because of ATI) on my Toshiba L305D-S5895, and suspend/hibernate both work just fine.

It's a puzzle...

:guitar:

---

### Post by Khufucius on 2009-10-21
Toshiba Satellite l305-S5957
Mobile Intel Graphics Media Accelerator 4500M with 128MB-830MB shared memory
Ubuntu 9.04

Same problem: I either close the screen or select "suspend" from the menu manually, and everything winds down as expected.  But when I try to start things up again, I get a blank screen, or a screen that looks like it can't start X (with the prompt seemingly JUST outside of the visible screen area, fuzzing in every once in a while).

A hard restart is the only option, but then everything is back to normal.

-Khufucius

---

### Post by ways on 2010-04-03
same here. toshiba satellite l450d, ubuntu 9.10.

---

