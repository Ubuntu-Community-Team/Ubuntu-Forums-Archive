---
title: "Whether to replace to keep modiofied .conf's"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by vsiege on 2009-03-27
I just upgraded from 7.10 to 8.04 and I came across a few messages that i 'guessed' on....
 I had updated 7.10 completely before the upgrade using update manager. The three questions concerned whether or not to replace the customized/altered configuration files of the following:
[INDENT]1. Apache
2. Samba
3. PHP[/INDENT]

I choose only to replace the Samba file with the new version while keeping the existing customized .conf files for PHP and Apache. Now i have to get Samba shares working again. After installation I received one error on restart regarding Apache - but never got it again. Heres the question (ha):

I figured since i am installing 8.10 at the moment - should I overwrite those files if it asks? do I do a three way merge? or should I always use the altered .conf's?

Ha that was more than one question

---

### Post by wkulecz on 2009-03-27
IMHO lacking complete info on application version changes across updates, to me its safest to backup the conf files in question and then replace with the new defaults during installation.  Then reconfigure each application to match your old setup using the backed up files as a guide.

OTOH if you have a non-standard boot arrangement (like mirrored system disk) I find it safest to keep instead of replace /boot/grub/menu.lst and then manually fix it before I reboot.  I've had issues with the /dev/md mapping change across kernel updates.

--wally.

---

### Post by vsiege on 2009-03-27
At the moment I have two HDs that are not in an array. I guess when those messages pop up again, I will do a replace. I already have backup (thankfully) of the originals and alternates.

So you are saying if I had any kind of RAID going- to not replace?

---

### Post by Mark Phelps on 2009-03-29
In my experience, anytime an upgrade warns about replacing config files, you should always allow it to install the newer version.  The simple solution (which I use) is to open a terminal and save off the existing config file to a different name before allowing its replacement.

I've experienced that every time I've done a kernel upgrade, and it was the easiest way to get back the customizations I'd made to menu.lst.

---

