---
title: "What did I do????"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by ppnl on 2009-04-03
Here is what I have. I had two harddrives in a raid array that was my windows xp. I installed a third harddrive. I went into bios and changed the boot order to boot on the third hard drive. I installed ubuntu on it.

Now when I switch boot order back to the raid and try to boot windows I get a grub error 25.

What did it do to my xp install?

---

### Post by cariboo on 2009-04-03
The Windows bootloader has to be on the first partition of the first hard drive, so by changing the boot order, Windows can't find the boot loader.

I  would suggest you change the boot order back to the way it was  then follow [thread=224351]this[/thread] to repair grub.

Jim

---

### Post by ppnl on 2009-04-03
> **cariboo907 said:**
> The Windows bootloader has to be on the first partition of the first hard drive, so by changing the boot order, Windows can't find the boot loader.

I  would suggest you change the boot order back to the way it was  then follow [thread=224351]this[/thread] to repair grub.

Jim

Ok thanks for the reply. But a few questions before I try this.

First why did the install mess with the MBR on my windows raid disks?  Thats a bad thing. I only wanted to install on the third harddisk without affecting anything else.

Your directions look like it will install grub on my windows install. I would rather simply rebuild my windows MBR if I can. This was just an experiment and I didn't want to change my windows install.

Finaly when I have third disk set to boot in bios I do get a boot menu from grub. Ubuntu generic, Ubuntu recovery and ubuntu memtest86. Windows isn't included here. If it just copies over the menu then I still will not have a windows.

I'm assumeing I still have my windows install and it is just the MBR that is cratered. What is a simple way to check this?

Anyway I'm going to try it. And I just noticed I taged this message ubuntu-mobile. I'm really haveing a bad day.

Anyway thanks

---

### Post by ppnl on 2009-04-03
Nope still getting grub error 25. Crap I'm lost.

---

### Post by ronparent on 2009-04-03
Just a guess before we have to get deeper. Use the windows install disk to 'repair' the windows mbr with the boot order is set to boot the windows array array. If that works we can give you instructions to install a grub mbr on your ubuntu drive. This can be configured to boot both ubuntu and windows whent the boot order is set to boot on that disk first!

---

### Post by ppnl on 2009-04-03
I can't find the stupid admin password!!!!

Beyond that I would still like to know why Ubuntu was messing with a disk it was not installing to. What did I do wrong?

I need to learn something from this disaster.

---

### Post by albinootje on 2009-04-03
> **ppnl said:**
> I can't find the stupid admin password!!!!


You can probably (I'm not a Windows-user) create an UBCD to fix this : [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

And there are bootable cdroms for cracking XP passwords.
[http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/)

---

### Post by ppnl on 2009-04-03
I didn't need a password because I never set one up. But I'm just reinstalling windows anyway. Windows security. 

But I need to understand why the install process messed with the windows MBR on a different disk anyway. This is just an experiment anyway so no big deal. But the point is to learn something.

---

### Post by ppnl on 2009-04-03
Ok I'm back where I was before installing ubuntu. Didn't lose anything. But before I try again would someone please explain how I mannaged to corrupt the windows MBR?

I have a windows 32bit xp install on a pair of harddrives raided together. I have another harddrive installed. I want to put 64 bit ubuntu on it. 

I do not want a boot menu. I just want to boot from the drive that is first in the boot order. I do not want them messing with each others MBR.

How about unplugging the windows disks while installing Ubuntu? It seems the only way to keep it safe.

As I said this is just a learning experiment. I can play with setting up boot menues after I figure out how to keep grub in a cage. So far Grub seems to be an evil beast that needs to be caged.

---

### Post by ronparent on 2009-04-03
It shouldn't have got to where it is but it did. You probably know better than anyone what you did. But having found myself in simular situations, after reacting to one install crisis after another I barely know what is up let alone what I did to get where I am! I still recommend that you restore the windows array boot record then we can focus on getting the ubuntu installation working.

---

### Post by albinootje on 2009-04-03
> **ppnl said:**
> I can play with setting up boot menues after I figure out how to keep grub in a cage. So far Grub seems to be an evil beast that needs to be caged.

I'm very surprised that this happened.

During the Ubuntu installation after partitioning there is a button which says "advanced" and there you can decide on which partition or MBR Grub will write to.

And for the record :
Microsoft has a record of more than 20 years of overwriting the MBR without asking and without informing and without options.

Years ago I bought the ancient DRDOS 6 and NovellDOS7 to play with (for fun), it was at least one of those two which gave information, and asked for making a copy of the MBR before overwriting it.

---

### Post by ppnl on 2009-04-03
Yeah maybe I wasn't clear but windows MBR is back and nothing important lost. The repair process seems to have taken out some of my hardware drivers but I'm reinstallintg as I need them.

I even have Ubuntu running in a way. The sound still will not work and when I tried to update it the GUI crashed on reboot and dumped me at a login prompt. I have no idea how to restart the GUI. But I can log in. I still have a great deal to learn before I'm comfortable with this.

I still do not trust grub. That was just evil behaviour. How can I trust it with something important if it does stuff like that?

---

