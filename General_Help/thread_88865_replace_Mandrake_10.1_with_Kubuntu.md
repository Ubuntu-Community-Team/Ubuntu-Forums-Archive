---
title: "replace Mandrake 10.1 with Kubuntu"
date: 2005-11-11
forum: General Help
---

### Post by Optiker on 2005-11-11
The previous posts by me were relative to my computer at work. This one is for my home computer, so the other posts aren't relevant yet, until/unless I run into the same problems.

My current home system has Mandrake 10.1 dual booted with WinXP. I don't recall why, or if it's the best way, but when I installed Mdk - in my relative ignorance - I installed it on two logical drives in the same extended partition as my Windows D-drive (my data drive for Windows). The result of that is that when I try to use the utility Ext2IFS to access the Mdk drive, I get a message saying it's not formatted and do I want to format it. That means that unlike my computer at work where I used Ext2IFS to clear my Mdk partition in preparation for installing Kubuntu, I can't do the same here.

I have a feeling that my partitions should be set up differently than to have both my Windows D-drive and my Linux drives in the same extended partition, but short of wiping all but my Windows C-drive and starting over, I don't know how to go about it. I also am hesitant to just dive in and install Kubuntu, because if I recall, when it gets to the choices of where to install Kubuntu, I recall not knowing what to do other than tell it to use unallocated space, and in this case, unless I clear the Mdk logical drive, there isn't any.

I don't have an adequate way to backup my D-dive, so anything I do needs to be highly likely to not corrupt or wipe my Windows D-drive. I realize that teh usual advice is to backup before doing major changes, but I just don't have a way to do it, so I take my chances and try to not do anything that's not pretty safe.

Any suggestions on how to proceed?

Thanks!
Optiker

---

### Post by mlomker on 2005-11-11
You should be able to figure out from within the installer what partition is the MDK one.  The default Ubuntu install is to just overwrite a partition but there's a custom option.  I have two partitions in an extended partition but they show up as separate paritions, so...

```

mlomker@mlomkernote:/$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            1217        7296    48837600    5  Extended
/dev/hda5            1217        7112    47359588+  83  Linux
/dev/hda6            7113        7296     1477948+  82  Linux swap / Solar

```

---

### Post by Optiker on 2005-11-12
mlomker...OK - I'll give it a try.

Do I need to somehow - maybe Knoppix - go in and delete the Mandrake contents before installing? As I mentioned, previously, I had used the Ext2 utility to clear the previous install before starting the new one. Sounds like I don't since the Kubuntu install will probably format the Mandrake partition. But I'd like to be sure.

Scary! Guess that's the bane of newbies...most anything that doesn't guarantee to leave everything else untouched is scary!  :)

Thanks...thought I wasn't going to get a reply...it was drifting down to later pages. I was beginning to think about replying myself just to get it back nearer the top.

Optiker.

---

### Post by Optiker on 2005-11-12
mlomker...argh! Can't do it. I started and got to the partitioning, and it was just too confusing to know for sure what was going to happen or not happen.

I even have a second hard drive that contains an old Windows installation that I'm prepared to format and use, but when I got down to the step of telling the installation to go ahead and partition, there were too many choices that said to erase the whole disk, and I wasn't clear on exactly what would happen.

The Kubuntu partitioner said it wouldn't erase existing data, so it looked like I couldn't install over the Mandrake installation, and it wasn't clear how to select it to clear for use. It would be nice if there was a s imple interface with the partitions/logical drives listed and allowing selection of one saying "install it here". No such luck...too simple. I realize that this opens the door to unintended consequences, but the more detail and choices given, the more confusing for somebody like me.

I just wish I could get back to two partitions on my HD - Windows C and D - and the rest unallocated so I could cleanly just tell it to use the free space. However, from what I've seen, resizing a partition can also be risky, and the extended partition that currently contains my Windows D drive (data) and the Mandrake and Linux swap partitions (logical drives) is too critical to risk losing the Windows D drive.

I'm close to giving it up and leaving Mandrake until I can backup my data, and clear that partition, or until something forces me to do a fresh start.

This begins to look like a rock and hard place deal. Fortunately my other posts deal with my computer aat work and it is partitioned correctly, and I've been able to work with it, and will keep Kubuntu on it. Also, my second home computer installed Kubuntu easily, but it's not the one I use most often, but an old 300 MHz Micron that's due for replacement.

Unless you have other suggestions, I very much appreciate your efforts on this issue and others I've posted. But maybe it's time to put it back on the shelf.

Thanks again!

Optiker

---

### Post by mlomker on 2005-11-12
Backing up your data first is the wisest thing to do.  I don't think it's realistic to have a custom install option that's also easy.  In order to make things simple they have to remove the ability to do advanced things that many installers (like myself) need to be able to do.  

I don't have Windows on my machines, so it's not so much of a problem.  I have a copy of VMWare (and other PC's at work) and load Windows in that when I don't have any other choice.

---

