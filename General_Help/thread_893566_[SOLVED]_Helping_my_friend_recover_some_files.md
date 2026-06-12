---
title: "[SOLVED] Helping my friend recover some files"
date: 2008-08-18
forum: General Help
---

### Post by mlilien on 2008-08-18
So, my roommate's computer crashed yesterday.  It apparently did this while he wasn't doing anything with it, so we don't know what could have caused it other than he's always had some issues with his computer.
What happens now is that it tries to boot into windows and after a couple seconds in the windows loading screen the whole computer reboots.

I tried using an ubuntu live cd to recover his school stuff, music, and firefox config files.  But when I try to mount the windows partition I get an ntfs_pread failed error.  I tried using gparted to repair the partition, but that also errored.

Any other ideas I could try?

Thanks

---

### Post by Awperator on 2008-08-18
Is it a laptop or a desktop?

If a desktop, have you tried to just remove the hard drive and connect it to another computer? Also, doesn't windows have a recovery option with the install disks? I think that they keep your files, but I am not certain.

---

### Post by adewale on 2008-08-18
Well i've had a similar problem, what i did was to get a windows install disk and opted for Repair. It gave me a command prompt where i ran CHKDSK. It fixed the ntfs and was able to boot back into windows

---

### Post by oldos2er on 2008-08-18
> **mlilien said:**
> So, my roommate's computer crashed yesterday.  It apparently did this while he wasn't doing anything with it, so we don't know what could have caused it other than he's always had some issues with his computer.
What happens now is that it tries to boot into windows and after a couple seconds in the windows loading screen the whole computer reboots.

I tried using an ubuntu live cd to recover his school stuff, music, and firefox config files.  But when I try to mount the windows partition I get an ntfs_pread failed error.  I tried using gparted to repair the partition, but that also errored.

Any other ideas I could try?

Thanks

 Sounds like the Win partition didn't shut down cleanly. Gparted recognizes this and won't mount the partition in an effort to preserve its data. Have your friend boot his Win CD (assuming he has one) and run chkdsk on the disk. Hope this helps.

---

### Post by mlilien on 2008-08-18
Thanks, that worked perfectly

---

