---
title: "Need to format my Windows partition"
date: 2009-04-20
forum: Hardware
---

### Post by DManX04 on 2009-04-20
While partitioning for my Ubuntu install, my Windows partition became corrupted. I now need to reinstall Windows, but my Vista re-install CD won't seem to work and my old XP disk won't either. I want to try clean installs after I format the partition, but I'm not sure what utility to use/how to do that in Ubuntu.

Any help?

---

### Post by whoop on 2009-04-20
run in terminal:
```

gksudo gparted

```

---

### Post by RedSingularity on 2009-04-20
Boot the Live CD and use gparted.

---

### Post by coffeecat on 2009-04-20
> **whoop said:**
> run in terminal:
```

gksudo gparted

```

Hmm. Not everyone wants to use the terminal when a couple of mouse clicks would do the trick.

**DManX04**, boot up from a live CD. Go to System > Adminstration > Partition Editor (Gparted), and create whatever partition(s), including NTFS, you need. The versions of Gparted that come with the 8.10 and 9.04 live CDs will certainly create NTFS partitions. I'm not sure about 8.04 (Hardy) but I would hope it does.

Or, if you want to reformat the corrupted Windows partition in a hard disc install of Ubuntu, first make sure you have both gparted and ntfsprogs installed (they don't come with a default install), and you will find Gparted in the same place in the menu.

However - what exactly do you mean by the Vista and XP discs not working? Are they not booting at all? It's a long time since I did an XP install and I haven't touched a Vista disc, so I can't remember how sophisticated the partitioner is, but I seem to remember it will reformat a partition it can recognise. Perhaps your Windows partition is so corrupted that the partition table entry is damaged. In which case gparted should give you a good visual check of what's going on.

---

### Post by DManX04 on 2009-04-20
The Vista disc is a re-install disc that Dell shipped with the laptop. When I try to use it, it says gets to a prompt that says "Completing Install" and then does nothing. I waited for about two hours twice now, and both times the screen eventually goes blank and won't come back on. After a reboot, the Windows Safe Mode menu comes up, but Vista won't ever load. I don't know if the disc is trying to copy and image or if just can't handle the multiple partitions, but it doesn't ever finish the install.

XP just won't install at all. I've changed my hard drive configurations in the BIOS to try and get it to work, but it just loads everything it needs and then goes to a blue screen saying that there was an error and windows is shutting down. It looks a lot like a memory dump shutdown that I used to sometimes get in XP and Vista.

Either way, neither will install. I know those probably weren't the best technical descriptions, but I'm not sure how else to explain it.

---

### Post by lisati on 2009-04-20
> **DManX04 said:**
> The Vista disc is a re-install disc that Dell shipped with the laptop. When I try to use it, it says gets to a prompt that says "Completing Install" and then does nothing. I waited for about two hours twice now, and both times the screen eventually goes blank and won't come back on. After a reboot, the Windows Safe Mode menu comes up, but Vista won't ever load. I don't know if the disc is trying to copy and image or if just can't handle the multiple partitions, but it doesn't ever finish the install.

XP just won't install at all. I've changed my hard drive configurations in the BIOS to try and get it to work, but it just loads everything it needs and then goes to a blue screen saying that there was an error and windows is shutting down. It looks a lot like a memory dump shutdown that I used to sometimes get in XP and Vista.

Either way, neither will install. I know those probably weren't the best technical descriptions, but I'm not sure how else to explain it.
I don't know about the DELL disks, but the Toshiba recovery DVD that came with one of my laptops didn't work after I'd installed Ubuntu until I renamed the proposed Windows partition. The "correct" volume label was buried in one of the files in the root directory of the DVD.

---

### Post by coffeecat on 2009-04-21
> **DManX04 said:**
> The Vista disc is a re-install disc that Dell shipped with the laptop. When I try to use it, it says gets to a prompt that says "Completing Install" and then does nothing. I waited for about two hours twice now, and both times the screen eventually goes blank and won't come back on. After a reboot, the Windows Safe Mode menu comes up, but Vista won't ever load. I don't know if the disc is trying to copy and image or if just can't handle the multiple partitions, but it doesn't ever finish the install.

I have no experience of Dell. My Sony Vista restore utility let me restore Vista to the C: partition I had resized without having to restore the restore partition all over again, but that doesn't help you.

Perhaps you're right in that it is getting confused by the multiple partitions. Perhaps the reinstaller needs to reinstall the hidden/restore partition that I believe Dell uses. My only suggestion is to wipe the whole disc, leaving no partitions. The easiest way is to use Gparted in the live CD and select 'create partition table' or something similar (I'm going from memory - I'm in MacOS atm). This will leave the whole disc unformatted but with a fresh partition table. Then see if the Dell installer can reinstate the partitions it wants.

Of course that means you'll have to shrink the Vista partition again and all the rest, but at least you'll get Vista back.

Sorry - no idea on the XP front.

---

