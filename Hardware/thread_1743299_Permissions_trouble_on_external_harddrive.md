---
title: "Permissions trouble on external harddrive"
date: 2011-04-29
forum: Hardware
---

### Post by Capt_Zaphod on 2011-04-29
Hello;

I'm running Lucid Lynx.

I have a Buffalo external hard drive with a msdos file-system & a total capacity of a terabyte.  I've only got 80gb on it.

All of a sudden, it's permissions changed to read only.  I've tried changing them back (through properties), but, a moment later it reverts itself.

Is there a fix for this?

Thank you;
~Z

---

### Post by NeilE888 on 2011-05-14
I had exactly the same problem (same OS etc,) , with a Buffalo USB drive becoming 'read-only', I didn't find a better fix, so copied the files to another location, reformatted the drive and then all was OK - I could write to the drive without problems.

Interestingly there were no read/write issues if I connected to a Windows XP Pc

Sorry it's not a cleverer solution.
                                     N

---

### Post by Darkness Des on 2011-05-14
The thing about NTFS (the ms-dos filesystem) is that it doesn't accept normal permissions that Ubuntu uses. It has its own permissions system that, last I checked, could only be changed by Windows.

More to the point, a lot of drives have a read only switch on them that prevent any data from being changed. Check for one of those.

---

### Post by Capt_Zaphod on 2011-05-14
> **NeilE888 said:**
> I had exactly the same problem (same OS etc,) , with a Buffalo USB drive becoming 'read-only', I didn't find a better fix, so copied the files to another location, reformatted the drive and then all was OK - I could write to the drive without problems.

Interestingly there were no read/write issues if I connected to a Windows XP Pc

Sorry it's not a cleverer solution.
                                     N

That's the trouble though...I've got no where to transfer all of my information too; in order to re-format.

Thank you;
~Z

---

### Post by Capt_Zaphod on 2011-05-14
> **Darkness Des said:**
> The thing about NTFS (the ms-dos filesystem) is that it doesn't accept normal permissions that Ubuntu uses. It has its own permissions system that, last I checked, could only be changed by Windows.

More to the point, a lot of drives have a read only switch on them that prevent any data from being changed. Check for one of those.

It's not NTFS though it's FAT 32 & I can't see how it changed all by itself & prevents me from changing back?

There's no switch.

Thank you;
~Z

---

