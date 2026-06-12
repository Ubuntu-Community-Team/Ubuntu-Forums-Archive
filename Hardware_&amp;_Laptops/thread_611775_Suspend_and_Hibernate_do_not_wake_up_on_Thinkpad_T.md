---
title: "Suspend and Hibernate do not wake up on Thinkpad T43"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by Redenbacher on 2007-11-13
I just installed Ubuntu 7.10 on my T34 and it will not wake up from hibernate or suspend. The sleep light just blinks and the fan keeps running, but does not awake when I push the power button. Any ideas?

---

### Post by d1ss0nant on 2007-11-13
I have a compaq R3000Z and I have an identical problem - when i try to wake from hibernate I'm greeted with a black screen & forced to restart (by powering down manually).  Many people I know have the same problem.  I am eager to find a fix for this as well.

---

### Post by Giradman on 2007-11-13
I installed Ubuntu 7.1 on an IBM TP X40 - tried 'hibernate' & 'sleep' modes w/o much success - did not seem to 'shut down' as expected - next day computer bottom was still warm; but the computer would 'wake up' for me - now I just 'shut down' & re-boot the next day - trying out a lot of other features, so this issue has been moved to the bottom of the list! :)

---

### Post by aethralis on 2007-11-13
Yes, suspend and hibernate are problems (here also with Lenovo 3000n100), but as they say, for windows it took 10 years to get it OK, so hopefully in some we have it too.

---

### Post by Redenbacher on 2007-11-13
Yea I found a bug on launchpad about a bunch of people having problems with suspend and hibernate most of them with the combination of fglrx + SLUB + ATI, or something of the sort (SLUB is the memory allocator, I think... and those who tried switching back to SLAB have had better luck (The memory allocator before gutsy?)). I've no idea how to switch back to SLAB, nor do I know how to stop the 'fglrx module' to stop loading. Besides, that would mean I have to give up compiz-fusion... I'd rather shut down!

 It's slapped on wishlist because we have to wait for ATI to fix the problem with their drivers.  Hopefully they're working on that!

---

### Post by spier on 2007-11-13
> **d1ss0nant said:**
> I have a compaq R3000Z and I have an identical problem - when i try to wake from hibernate I'm greeted with a black screen & forced to restart (by powering down manually).  Many people I know have the same problem.  I am eager to find a fix for this as well.

Hi, this may not be related at all, but while trying to fix a minor issue while resuming from a suspend, I installed (thru synaptic) hibernate package, that start causing the blank screen. After removing hibernate, reinstalling gnome-power-manager and restart, I got suspend/hibernate/resume fixed.

HTH

---

### Post by romeyde on 2007-11-13
Thanks for the suggestion, unfortunately, doesn't appear to have helped in my case.  My PC will suspend just fine, but then won't wake fully back up.   End up having to reset.   Several threads about this issue going on.

Tried installing the hibernate package, then removing it and reinstalling the gnome power package.  Restarted, suspended, and no wakey wakey again...

---

### Post by AIXpi on 2007-12-01
> **Redenbacher said:**
> I just installed Ubuntu 7.10 on my T34 and it will not wake up from hibernate or suspend. The sleep light just blinks and the fan keeps running, but does not awake when I push the power button. Any ideas?

I have exactly the same problem on my T43. I found[ this bug report ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/155037")for the 2.6.22 source, but there's no information about how and when this is meant to be fixed.

---

### Post by mperry on 2007-12-05
I just installed Xubuntu 7.10 on my T43 and initially had the same problems.  I don't know that its completely fixed; but I'll tell you what I did.  First off, I removed acpi-support from the mix because it seems to me that many of the issues I had was with those scripts and events.  I also don't understand all of them and I seriously doubt that they all do anything worthwhile.  Next I installed pm-utils all by itself.  Suspend started working a bit better.  I then installed uswsusp because pm-utils suggests that package.  I had to edit /boot/grub/menu.lst and add in a resume line and also make the line right in /etc/uswsusp.conf for the swap location.  Somewhere inbetween I broke usplash.  

At this point on the T43, I have an empty /etc/acpi directory for the most part and HAL is driving pm-utils and somewhere uswsusp.  Does it work now?  I ain't sure; but it seems to do a bit better on individual restores from suspend.  My main issue, and its reported throughout the forums, is that suspend results in a laptop with either resume not working or the suspend not doing anything.  At this point, the suspend works and I've tried a few longer ones and it works.  I'm waiting to see after an evening of suspending the laptop.

Note that you do not lose any functionality and you can suspend and hibernate still.  If you just install pm-utils, it may be the suspend works with a lid close but starting again by opening the lid does not seem to.  I had to plop the power button.  After installed uswsusp and getting a new initrd it all works now.

---

