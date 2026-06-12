---
title: "xorg on an old intel 815"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by CsabaBo on 2009-04-07
Hi!

 I'm trying to install Ubuntu on an old PIII [Sony Vaio Notebook, model: PCG-FX190,]("http://esupport.sony.com/US/perl/swu-list.pl?mdl=PCG-FX190&region_id=1") that [ got shared video memory]("http://www.docs.sony.com/release/specs/PCGFX190_mksp.pdf"), FSB: 100 Mhz.
 Problem is that I get vibrantly distorted screen only at 800x600 screen resolution, and black frame, that is changing with the mouse movements and hard drive activity. --it's hardly usable.
 I have tried 8.10, and the 9.04 also with the same experience.
 There are Intel .rpm binary "drivers" but for the older XF86 only.
 Can someone please advice..
 Thank You in advance!

Cs.%

---

### Post by upchucky on 2009-04-07
ubuntu too much for this machine, try puppy linux or other such small footprint versions, there is even a version of tiny office that should work with a pc this small.

---

### Post by CsabaBo on 2009-04-07
I think it`s only a mater of the xorg-intel! That prevents me from using Ubuntu? What is the guarantee, that other current distro's xorg binary would run better on this i815? Thanks anyway for the idea!

---

### Post by upchucky on 2009-04-07
the only way to provide a guarantee is to experiment to a solution. 

the reason suggested small footprint version is because this machine was designed with windowsME in mind, it is a very low end pc with the shared memory you are gonna have trouble with the processor doing double duty.
Ubuntu is happy with 1ghz processor and 512 ram.

However Ubuntu can be stripped down to work, this just takes a bit of planning and lots of work.

---

### Post by CsabaBo on 2009-04-08
Only have one life so one distro should be enough. I used to use Debian and derivations of it. Shold I remain at windowsxp? That is running fine on this hardware. 
:lolflag:

---

### Post by upchucky on 2009-04-08
debian custom built will run fine on that machine, ubuntu has a lot of bells and whistles, which is why i said to strip it down, Ubuntu is built on debian.

you must remember that with anything windows, u gonna need tons of third party support software just to keep windows running, never mind that windows is designed to slowly self destruct.

---

