---
title: "How to format Ubuntu/linux?"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by Estroyer on 2009-10-02
I want to switch the OS of my two laptops (Windows <---->  Ubuntu)
After an entire day of downloading, going trough several forums and burning three cd's with what I hoped would be the aquired software, I'm throwing my towel in the ring: I just can't get my linux operated system formatted or get it booted from a windows cd!
There are several topics on this subject but they all are slightly different from my problem: I don't have a floppy drive and I am quite a noob when it comes to Linux so that isn't making it any easier...

So please help me on to how reinstall windows on this laptop...getting Ubuntu on the other machine was easy peasy off course...but the other way around seems like mission impossibly so far.

Thanks in advance!

---

### Post by earthpigg on 2009-10-02
on the machine you want to put windows on:

run the Ubuntu live cd, system -> administration -> partition editor -> delete all partitions -> apply...

...now try the windows cd.

it still doesn't work, try creating a new fat32 or ntfs partition and then try it.

---

### Post by Estroyer on 2009-10-02
Thanks, I'll try it and get back to you how it worded for me!

***EDIT***

I can't get my laptop to run from the Ubuntu live cd.
When I go to:
Places->Ubuntu cd I see it opens the cd and I see some files.
I try to double click wubi.exe but then I get:

[/media/cdrom0/wubi.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/wubi.exe or
          /media/cdrom0/wubi.exe.zip, and cannot find /media/cdrom0/wubi.exe.ZIP, period.

Did I burn the cd the wrong way?

---

### Post by Estroyer on 2009-10-02
Update above :)

---

### Post by earthpigg on 2009-10-02
***_boot_*** from the Ubuntu LiveCD, just like you do when installing Ubuntu.

:D

---

### Post by oldos2er on 2009-10-02
> **Estroyer said:**
> Thanks, I'll try it and get back to you how it worded for me!

***EDIT***

I can't get my laptop to run from the Ubuntu live cd.
When I go to:
Places->Ubuntu cd I see it opens the cd and I see some files.
I try to double click wubi.exe but then I get:

[/media/cdrom0/wubi.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/wubi.exe or
          /media/cdrom0/wubi.exe.zip, and cannot find /media/cdrom0/wubi.exe.ZIP, period.


 wubi.exe is meant to be run under Windows, not Ubuntu.

---

