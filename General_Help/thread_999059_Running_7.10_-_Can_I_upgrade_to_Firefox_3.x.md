---
title: "Running 7.10 - Can I upgrade to Firefox 3.x ?"
date: 2008-12-01
forum: General Help
---

### Post by davexnet on 2008-12-01
Hello, I'm fairly new to Ubuntu/Linux.

This 7.10 version I'm running, seems stuck with old releases,
such as Firefox 2.x, Amarok 1.48,etc,etc.

How do I update to new releases? Do I have to upgrade to Ubuntu 8.x first?

Secondly, Amarok says it is using KDE 3.5.8 - isn't that the desktop
manager?  I thought I was using Gnome with Ubuntu 7.10?

Maybe I'm missing some concepts in my understanding.  Any tips appreciated.
Dave

---

### Post by glotz on 2008-12-01
Hey Dave!

To get the latest versions you'll have to install them outside the package manager. (or find some repo which serves you the latest versions, not something I'd suggest to a new player) Here are Firefox 3 system reqs. [http://www.mozilla.com/en-US/firefox/system-requirements-v3.html](http://www.mozilla.com/en-US/firefox/system-requirements-v3.html)

You can use e.g. Synaptic to check if you have new enough libraries.

And Amarok, that's a KDE app so it uses KDE libs. Those got sucked in when you installed a KDE app.

Any particular reason for not installing say the latest LTS version?

---

### Post by lavinog on 2008-12-01
> **davexnet said:**
> Hello, I'm fairly new to Ubuntu/Linux.

This 7.10 version I'm running, seems stuck with old releases,
such as Firefox 2.x, Amarok 1.48,etc,etc.

How do I update to new releases? Do I have to upgrade to Ubuntu 8.x first?

Yes, it would be best to upgrade to 8.x if you want more recent versions of programs.
Generally updates to programs do not update them to the latest version...they are bug fixes/security fixes.

---

### Post by davexnet on 2008-12-01
lavinog and glotz,
thanks for your replies.   
Right now in the update manager, it offers 8.04 LTS.
I would like to update, but...

Because I had Windows Vista and XP setup as dual boot and 
Ubuntu added as a third, I put Ubuntu's boot manager (grub?)
in Ubuntu's partition and not in Master Boot Record.
So now when I boot up, I get Vista boot loader and menu
with Ubuntu added an option.  I think I added it manually but
can't remember the details.

It's the concern of destroying this setup that stops me updating.

---

### Post by glotz on 2008-12-01
I don't think upgdating would give you any trouble with that. And if it should I think the vista install media contains a way to reinstall the evil vista drm lovin mbr. At least xp's did.

---

### Post by lavinog on 2008-12-01
Actually I don't think upgrading will replace your mbr...it just installs new packages on the already setup file systems.
It will update your grub menu, but still leave the old entries.
EDIT: of course make sure you have time to deal with hiccups during the upgrade.

---

### Post by davexnet on 2008-12-01
OK - thanks for the info.  I may give a try.

Regarding the boot loader location, I've got a file, linux.bin,
in my c: primary windows partition.  512 bytes.
This is the thing pointed to by Vista's boot menu Ubuntu entry.

I created by using this command
dd if=/dev/hda2 of=/mnt/floppy/linux.bin bs=512 count=1
as mentioned in this article:
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

I suppose if the LTS update changes this area, I might need to recreate this file - or may be not?

---

