---
title: "Faulty installation"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by hershmab on 2009-07-07
I seem to have installed Ubuntu 9.04 not only in the wrong way but also on the wrong drive!

I run Windows XP Pro on a PC and wanted to try out Ubuntu without removing Windows. I followed the appropriate instructions in the Community Support Documentation and created an ISO-formatted disk of the Ubuntu download. I restarted my PC and booted from that disk, choosing the option to install Ubuntu in parallel with Windows. 

That all worked correctly, but I quickly realised that Ubuntu had created a boot partition on my external, removable USB drive instead of on the internal hard drive - something that was very unwelcome as I do not want to need the external drive always on line just to boot up the system. I use it simply as a backup drive.

On looking around for means to reverse this, I found instructions on how to download GPartEd and use it to remove the Ubuntu partition and (I hoped) uninstall Ubuntu. So I did all that, deleted what looked to me like the right partition and restarted the PC. Unfortunately it would then not boot up at all - the start-up stopped with a "Grub Error 17" (I think) message. Putting the external drive offline mad no difference - I just could not boot up at all.

In order to be able to use Windows and try Ubuntu, I had to go through the initial Ubuntu installation procedure yet again and live with the fact of booting from the external drive. 

How can I uninstall Ubuntu completely and return both the PC and also the external drive to their original states?

---

### Post by PureLoneWolf on 2009-07-07
Essentially you need to get rid of Grub - If you boot from the Windows XP cd, you can get to the recovery console and run the fixmbr utility.

This should put the windows boot loader back in place - You can then boot from the livecd again and remove the ubuntu partition that you created (if the windows disk manager won't do it...I had problems in the past)

Hope that helps

---

### Post by hershmab on 2009-07-08
> **PureLoneWolf said:**
> Essentially you need to get rid of Grub - If you boot from the Windows XP cd, you can get to the recovery console and run the fixmbr utility.

This should put the windows boot loader back in place - You can then boot from the livecd again and remove the ubuntu partition that you created (if the windows disk manager won't do it...I had problems in the past)

Hope that helps

Two derived questions:

[LIST=1]
[*]My Windows is currently XP PRO SP3 but I do not have the CD from which I installed it, only the CD for my original XP Home SP1. Will that still work without downgrading the OS?
[*]By **livecd** do you mean the ubuntu ISO-formatted installation cd?
[/LIST]
Thanks.

---

### Post by PureLoneWolf on 2009-07-08
You should be fine using the original XP disc to perform fixmbr, just don't do a full repair.  I am not aware of any difference between any XP versions mbr.

Yep, the livecd is the bootable ubuntu cd

---

