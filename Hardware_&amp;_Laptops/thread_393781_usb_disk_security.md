---
title: "usb disk security"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by colsinc on 2007-03-26
Hi all

I have a usb disk which has up to now been used on a windows computer.  It is partitioned into an unsecured 1.44Mb partition and the rest of the disk into a secure partition.  When used on Windows the 1.44Mb partition shows up as a floppy disk, and contains DiskPro software which asks for a password to allow the main partition to be accessed.  

The small partition mounts fine on Ubuntu, but the software won't run on wine, and I can't find another way to mount the large partition, as it doesn't even show up in Computer.  When I ran System>Administration>Disks it hogged my processor and wouldn't fully open (ie, the window stayed gray and the cursor loop-de-looped as it is wont to do).  Is there some other way I could circumvent/satisfy this password protection?

thanks in advance :KS

---

### Post by megamania on 2007-03-26
> **colsinc said:**
> Is there some other way I could circumvent/satisfy this password protection?

If the disk is encrypted, it would be a paradox to be able to circumvent the password protection in an easy way.

If the program you need to open the disk doesn't run in wine, I think the best (only) solution is to attach the drive to a Windows computer and convert it to an unencrypted disk.

---

### Post by kidders on 2007-03-26
> **megamania said:**
> If the disk is encrypted, it would be a paradox to be able to circumvent the password protection in an easy way.That seems sensible.

It might be worth mentioning that once you've decrypted your USB device, there are plenty of open (ie not proprietary) ways of re-encrypting it, at least *some* of which will surely play nice with Windows. It would be ideal if you didn't have to give up your privacy, in exchange for the ability to use your disk with more than one OS.

Compatibility is one of the many problems that tend to plague users of closed software. :-(

---

### Post by colsinc on 2007-04-02
thanks for the ideas everyone.  I've just copies the files through a windows installation I have lying around

---

