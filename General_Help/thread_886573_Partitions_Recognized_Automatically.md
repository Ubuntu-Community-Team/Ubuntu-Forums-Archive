---
title: "Partitions Recognized Automatically?"
date: 2008-08-11
forum: General Help
---

### Post by raywood on 2008-08-11
I'm using Hardy 8.04 on a dual-boot WinXP system with multiple hard drive partitions and an external USB drive.

Somebody advised me to add a couple of lines to /etc/fstab that, I guess, forced recognition of my external drive. Those lines look like this:

> # /dev/sdb5
mount /dev/sdd5 /media/OFFSITE ntfs-3g force 0 0

I think the first of those two lines must contain a typo -- I think I probably should have typed sdd5, not sdb5.

My question:  can I do the same thing for each of my hard drive partitions?  One goal would be to have them always visible from within Ubuntu. 

Another goal:  I'm using VMware Workstation, and it sometimes seems to forget that I have those other partitions.  So I have to manually add them again in VMware and then map them in the Windows guest operating system within VMware.  I'd rather automate that if possible.

I posted the question on a VMware forum but got no response.

If I use something like those two lines for each of my other partitions, should I include the "ntfs-3g force 0 0" language?  Where would I find an explanation of what that language is for?

If I add another partition in the middle somewhere, I assume I'll have to rewrite some of these lines accordingly.

The goal of this enterprise would be to make my various hard drive partitions automatically visible to VMware. But perhaps there is an easier way to do that?

Thanks in advance for suggestions.

---

### Post by munkyeetr on 2008-08-11
Your /etc/fstab line is going to want to look more like:
```

/dev/sdd5 /media/OFFSITE ntfs-3g defaults 0 0

```

Here's some more information about the /etc/fstab file for you: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

