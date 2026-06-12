---
title: "laptop cd drive doesn't work until replugged"
date: 2008-08-05
forum: Hardware
---

### Post by nc_jed on 2008-08-05
folks,
my dell inspiron 4000 has one of those moduler hotswappable cd-rw drives.  i'm running xubuntu 8.04 (xfce) and have noticed that the cd drive doesn't mount/become available until i physically unseat/reseat the drive.  when i do this, i hear it spin up, read the disc, etc.

what options do i have to allow the machine to just read the disc when i insert it?

jed

---

### Post by snowpine on 2008-08-05
> **nc_jed said:**
> folks,
my dell inspiron 4000 has one of those moduler hotswappable cd-rw drives.  i'm running xubuntu 8.04 (xfce) and have noticed that the cd drive doesn't mount/become available until i physically unseat/reseat the drive.  when i do this, i hear it spin up, read the disc, etc.

what options do i have to allow the machine to just read the disc when i insert it?

jed

I have an old Dell as well, and while I didn't have your exact problem, it would sometimes lock up at boot time. My solution was to add 'all_generic_ide' to the boot kernel line (at grub, press esc then e)--give it a try! You could also check your bios settings; there's a setting in there that governs the behavior when drives are swapped in/out of the bay. Good luck!

---

### Post by nc_jed on 2008-08-05
> **snowpine said:**
> I have an old Dell as well, and while I didn't have your exact problem, it would sometimes lock up at boot time. My solution was to add 'all_generic_ide' to the boot kernel line (at grub, press esc then e)--give it a try! You could also check your bios settings; there's a setting in there that governs the behavior when drives are swapped in/out of the bay. Good luck!

Thanks, I'll give that a try.  By chance, does this address the 'hdc not ready' messages that flood dmesg?

---

### Post by snowpine on 2008-08-05
> **nc_jed said:**
> Thanks, I'll give that a try.  By chance, does this address the 'hdc not ready' messages that flood dmesg?

My boot error message was "buffer i/o error on device fd0, logical block 0" and the reason I think it's possibly related to your problem is that physically removing the CD drive from the bay made it go away. So it is some kind of conflict between ubuntu and the Dell swappable drives. Good luck and sorry I don't have more. You might try searching the bugs over at launchpad.

---

