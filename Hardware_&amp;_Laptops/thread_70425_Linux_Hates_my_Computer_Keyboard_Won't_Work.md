---
title: "Linux Hates my Computer: Keyboard Won't Work"
date: 2005-09-29
forum: Hardware &amp; Laptops
---

### Post by Poseidon on 2005-09-29
I am using Ubuntu 5.04 for AMD64 on DVD.  My computer is a fairly new Medion desktop with an Athlon 64 3200.

I had no problems going through the partitioning, but the first problem I encounter, during the part of the installation with the DVD in the drive is that Linux does not recognise my hardware clock, so no proper time gets set.  Once I removed the DVD and restarted to continue the installation...nothing.  I mean, the first step shows up on my monitor, but I can't use my keyboard at all!!  All my settings for the keyboard were entered correctly (I tried a number of times).  I also tried with a different keyboard from my old computer (which worked fine with Linux) and still nothing.  I tried with Fedora Core and the problem is exactly the same: no hardware clock recognition, and keyboard won't work after the DVD-supported phase of installation.  I tried with a Debian net install and it froze early on during the hardware recognition early on.

What the heck is going on?  Is my computer designed to be Linux-proof or something?  Windows has no problems with PS/2 devices or hardware clock.  Any advice would be much appreciated.

---

### Post by andlinux21 on 2005-09-29
I had a similar problem with it detecting my mouse but i just blamed it on having a cheap motherboard (PC Chips K7 848A) so needless to say I am going to get another board.

---

### Post by Poseidon on 2005-09-30
Hmm, I found out the problem was actually due to a minor error in my bios.  Disabling the USB mouse/keyboard fixed it, and I've got Ubuntu running okay now.

---

### Post by paranoid on 2005-09-30
Man, I know how you feel, linux hates my computer aswell,

Mandrake 9.2 -no sound (fixed it though)
then freezes after 5min of use ( never fixed just installed ubuntu 5.04)

Ubuntu - 
grep error 18 (installed lilo instead)
no mouse ( not yet sorted)
no sound (not yet sorted)
my dual boot is no more need to configure lilo better 

but the good thing is I'm learning alot

---

