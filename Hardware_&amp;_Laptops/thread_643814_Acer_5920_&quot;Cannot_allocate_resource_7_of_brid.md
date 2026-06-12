---
title: "Acer 5920: &quot;Cannot allocate resource 7 of bridge...&quot;"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by Bartender on 2007-12-18
Used Ubutu 7.10 alt-install CD for this Acer laptop.  Get a quick display "Cannot allocate resource 7 of bridge..." something or other, several alphanumeric characters after the word "bridge".  Goes by too quickly to read it.  Several lines, with 7, 8, and 9 listed and repeated.
There are some old threads on this, one suggesting a bios update, but flashing the bios is not a task to be taken lightly.  'Sides,this lappy is brand-new.
Although Gnome desktop malfunctioned the first ime (desktop came up but very limited functionality) rebooted and it works fine.

PCLOS 2007 LiveCD doesn't give same error message.  
Mint does.  No surprise there, I guess.

Some of the old threads indicate the users couldn't find anything actually wrong once the OS was up and running, so they're just living with the error message.  
I think that would get really annoying.

---

### Post by errenay on 2007-12-22
I have the same issue with Kubuntu 7.10, but apart from this message, everything works fine...

---

### Post by bs.it on 2008-01-02
I had this same exact problem with kubuntu, ubuntu 6.06, 7.10...etc..

But what finally fixed it for me is I installed ubuntu feisty which I believe is 7.04 and no more error messages :)
Hope that helps .

---

### Post by Ludwix on 2008-01-08
I've got the same error messages in my dmesg:

[   13.824082] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.824086] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   13.824201] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   13.824314] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   13.824426] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   13.824539] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   13.824652] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   13.824765] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.3
[   13.824878] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
[   13.824990] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.3
[   13.825102] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.5
[   13.825215] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.5
[   13.825327] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.5

And I do not know what the solution might be

Greetz

---

### Post by Bartender on 2008-01-09
Thanks, Ludwix -
I forgot the terminal command so I could look at the messages...

---

### Post by crispben on 2008-01-11
I have an Acer 5610Z, I also get a similar error with Ubuntu 7.10 (i get error region 7, and 8, same errors you guys are getting).  In 7.04 I got no such error, but when I updated to 7.10 it was there.  I cannot see anything wrong with OS at all, in fact many more things work better from the upgrade.  The built in media card reader works now, it didn't in 7.04.  So my suggestion is to live with it, the error message is displayed for a total of 2 seconds, and to my knowledge there is nothing wrong.

I could very well be mistaken and if there is something wrong then I'd like it fixed too, but I have seen no such problems thus far.

Unfortunately I think I'm going to have to reinstall and do a dual-boot, because there are a few Windows ::gag:: programs I still need to use and they don't seem to work well/at all with WINE, of course I'm a pretty big newbie with Ubuntu, not to mention Linux command line and such, so it may just be a learning curve.....thats why I'm going for the Dual.

---

### Post by Bartender on 2008-01-11
crisp -
I know what you mean.  It hurts to admit that windows does some things better.  But facts are facts.

I'm glad I'm dual-booting.  Otherwise I'd have nothing to compare to.

With my Acer 5920:
- Wireless Intel 4965 card works, but less than half the speed of same card in vista.
- DMA doesn't seem to be working at all in 7.10.  Commercial DVD's are unwatchable.  vista works fine.
- Left speaker doesn't work at all.  Tried alsamixer, "Sound", gnome speaker applet, can't make it work.
- Dual monitor works, but only as mirror.  Intel drivers in vista offer much more options.
- A few other relatively minor things, but I didn't expect perfection.

Crossing my fingers that 8.04 will address all or most of these problems.

---

