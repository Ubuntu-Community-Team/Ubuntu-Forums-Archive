---
title: "CD filesystem"
date: 2010-03-18
forum: Hardware
---

### Post by kid1000002000 on 2010-03-18
This should be a fast solve for somebody.

What is the default filesystem for a CD that is burned in ubuntu?  Will it mirror the hard drive, rendering the cd unreadable in a windows drive, or is there a CD standard that will work cross-platforms that I have been thus unable to discover?

---

### Post by norseman-has-a-laptop on 2010-03-18
well what are you doing first

---

### Post by Goveynetcom on 2010-03-18
> **kid1000002000 said:**
> This should be a fast solve for somebody.

What is the default filesystem for a CD that is burned in ubuntu?  Will it mirror the hard drive, rendering the cd unreadable in a windows drive, or is there a CD standard that will work cross-platforms that I have been thus unable to discover?
well, the original CD works as a bootable CD or in windows. If you want to mirror a hard drive, I can't help you there, but I don't think it will be bootable, another computer will just read it as a disc with data files on it. If you want to just back up all your current data, why don't you just run a command from the root terminal to back up your main '/' directory to like a tarball?

There are numerous commands you can do for that, example:
here is a somewhat messy command, put it'll get the job done:
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/home /

```

You want to ignore the first few directories, if you plan to restore. You can always add more directories in that format. And you might want to take out the exclude home line, I just did that for a recent backup, because I have gigs worth of stuff in my home directory.
Again, it's best to be root, and go to the main '/' directory if you want a full backup of the system.

---

### Post by cchhrriiss121212 on 2010-03-18
I think what he wants to know is whether a cd burned in ubuntu will carry the ext4 file system. I am fairly certain that it doesn't but I know there are problems when trying to view video dvds burned in ubuntu on a windows machine. I think all cds use something called cdfs.

---

### Post by Grenage on 2010-03-18
Generally, ISO 9660.  This will work on just about any computer that can read discs.

---

### Post by srs5694 on 2010-03-18
It depends on how it's done, but with typical tools, Grenage is correct. I'll add that Linux CD-creation tools provide options to add to ISO-9660. You can add Joliet (long filenames in Windows), Rock Ridge (long filenames, permissions, and ownership in Linux/Unix), HFS (long filenames in Mac OS), UDF (the next-generation optical disc filesystem, providing long filenames on many OSes), and various different levels of ISO-9660 (8.3 filenames or single-case longish filenames). Precisely how you activate these different features depends on the specific CD-burning tool you use.

---

### Post by kid1000002000 on 2010-03-19
thank you all.

---

### Post by soltanis on 2010-03-19
ISO 9660.

Someone beat me to it. But just to be extra sure.

---

