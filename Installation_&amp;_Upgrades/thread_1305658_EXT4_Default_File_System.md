---
title: "EXT4 Default File System?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by seanj on 2009-10-30
I read in the 9.10 release notes that the default kernel can cause file corruption on an EXT4 file system. Is EXT4 the default file system in a new install? If so, what a disaster.

Edit: I said 9.04 when I meant 9.10, sorry.

---

### Post by richlyn9 on 2009-10-30
i think we get an dropdown option to choose others (i installed the RC which gave me an option to use ext3)
Yes ext4 seems to have issues.

---

### Post by kaibob on 2009-10-30
> **seanj said:**
> I read in the 9.04 release notes that the default kernel can cause file corruption on an EXT4 file system. Is EXT4 the default file system in a new install? If so, what a disaster.
I wasn't aware that ext4 was the default file system in 9.04. It is in 9.10 when doing a clean install but you can easily change that to ext3 if you wish.

---

### Post by Earl_Maroon on 2009-10-30
I have been using ext4 since the release of Jaunty and have had no trouble with it. It seems perfect;y stable to me.

---

### Post by recluce on 2009-10-30
Looking at the problem reports with EXT4 right now, I would not use 9.10 with EXT4 at this moment. Which gives you the following options:

_1. Clean Install_
You can easily select a different file system from partition manager for your root, just be sure to set partitions manually. You probably should consider any other EXT4 partitions you may already have (seperate home directory, external drives etc). If you have any EXT4 partitions and you handle files larger than 512MB, you might just want to wait.

_2. Upgrade_
If you don't have EXT4 partitions at this time, you don't have a problem, 9.10 will install to the existing root partition (EXT3, reiser, whatever). If you do have any EXT4 partitions, you might want to wait for a fix to 9.10. See above.

> **Earl_Maroon said:**
> I have been using ext4 since the release of Jaunty and have had no trouble with it. It seems perfect;y stable to me.

The bug reported is specific to Karmic, so this is not a valid argument.

---

### Post by bumanie on 2009-10-30
I am using ext4 on 64bit and 32bit jaunty + am using it on 64bit karmic. ext4 is regarded as stable and I have not had a problem with it on either of the 3 installations.

---

### Post by macogw on 2009-10-30
> **recluce said:**
> 
The bug reported is specific to Karmic, so this is not a valid argument.

Er...the OP said they were reading 9.04's release notes though...  Though in the case of the 9.10 file corruption issue: only on extremely large files, like the Kubuntu ISO I downloaded today.  Your documents and config files and things? Those are fine.  What I'd recommend is ext4 for / and ext3 for /home if you've got very large files to worry about.

---

### Post by seanj on 2009-10-30
> **macogw said:**
> Er...the OP said they were reading 9.04's release notes though...
Sorry about that. I meant 9.10. I handle a lot of really large files on my system, so the bug scared me. If I convinced my friends to use the new Ubuntu, it would by default be very hazardous to their files. Not pretty :( Myself, I will use EXT3 when I install. Thanks guys!

---

