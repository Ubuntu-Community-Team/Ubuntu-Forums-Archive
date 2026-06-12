---
title: "Installation on external HD - Grub Issues"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by TommyC on 2009-03-26
First, I'd like to say I have searched and tried many of the things I've found, but I'm not succeeding.  Having my own thread I feel like I can get a little better help on my specific problem.

I'm using a Fujitsu 120gb HD that I pulled out of my old Macbook and mounted in an enclosure.  It's hooked up to my 32bit Sony VAIO via USB.

Currently, I'm running off of the Live CD as I'm getting the GRUB Error 21 when I try booting regularly.

I installed Ubuntu 8.10 to my External 120gb HD using the second option in the installation (I forget what it said exactly, but it was basically don't partition any drive, use the entire drive for Ubuntu.)  After doing all this, the computer seemed to work fine, until I restarted without the CD in, I got the Grub Error 21.  

In BIOS I have it set to boot the External first, then internal.  After unplugging the external, I tried booting again, and still got the Error 21.  Plugged the external back in, Error 21.  I ran it with the CD and ran from the Live CD and it worked fine, restarted the computer and took the CD out, and with the external still plugged in, my computer booted to my internal, booting Windows Vista.  All my files are still there and it works fine, so it looks as if nothing was edited within my internal-- so why won't it boot with the external unplugged, after installing ubuntu?

Tried reinstalling Ubuntu on the external again and got the same errors.  Ran the Live CD and got the same outcome.

All I want is to be able to have it installed on the external, and have the external boot when I want it to, and have the internal windows boot when I want it to.  I figured it would've been fairly simple, just unplug the external and it will bypass booting to the external, but no.

Any help is appreciated.

---

### Post by Pumalite on 2009-03-26
Edit your external drive's menu.lst and make 'boot' and 'groot' (hd0,0)
Then try again.

---

### Post by TommyC on 2009-03-26
Went in and edited menu.lst, there was no editable boot= in the document?  Edited groot to (hd0,0) then wasn't able to save without permissions.  Tried to change the permissions and I wasn't an owner, so I went on searching for that problem and while I was at it I tried reinstalling again.

At step 6 or 7 on the installation, I clicked advanced and made sure the Bootloader was being installed to sdc (the external.)  I restarted and now windows will boot, but the external will not boot.  BIOS is set correctly, it's just not being recognized.

---

### Post by Pumalite on 2009-03-26
Sorry;I'm in my Mac. Must be 'root'

---

