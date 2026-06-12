---
title: "Can't see Windows Partition from Ubuntu 8.04"
date: 2008-10-05
forum: General Help
---

### Post by Oziyak on 2008-10-05
Hi all,

I've installed ubuntu recently and am still getting the hang of some things.  My original operating system is XP... and I've grown tired of it bogging down on me and always needing a reformat.  I do however want to keep it as part of my system for certain programs which I'm usure (or unaware) that I can run on ubuntu as well.

I had originally installed XP on one drive.  And when I installed ubuntu on a separate drive I installed the GRUB bootloader onto the windows drive.  Now that I'm working in Ubuntu, I'd like to access some files on the XP harddrive but I always get an error when trying to do so. I get an error messaged saying that I can't mount the drive because NTFS is marked to be in use?

Hoping someone can shoot me an easy and painless fix :)

thanks

---

### Post by ajmorris on 2008-10-05
> **Oziyak said:**
> Hi all,

I've installed ubuntu recently and am still getting the hang of some things.  My original operating system is XP... and I've grown tired of it bogging down on me and always needing a reformat.  I do however want to keep it as part of my system for certain programs which I'm usure (or unaware) that I can run on ubuntu as well.

I had originally installed XP on one drive.  And when I installed ubuntu on a separate drive I installed the GRUB bootloader onto the windows drive.  Now that I'm working in Ubuntu, I'd like to access some files on the XP harddrive but I always get an error when trying to do so. I get an error messaged saying that I can't mount the drive because NTFS is marked to be in use?

Hoping someone can shoot me an easy and painless fix :)

thanks

Hi there,
It is easier if you use the ntfs-3g driver, instead of the ntfs kernel driver :) so if you are mounting the partition manually, use -t ntfs-3g  or if it is in the automatic process, in /etc/fstab, where the partition type is set to ntfs, change it to ntfs-3g

that should solve that error :)

AJ

---

### Post by mssever on 2008-10-05
Actually, Hardy uses NTFS-3G by default. You didn't specify your exact error message so I can only guess, but a common problem is that if the NTFS partition is marked dirty, Linux can't mount it. The solution is to boot into Windows twice, shutting down properly both times.

---

### Post by ajmorris on 2008-10-05
> **mssever said:**
> Actually, Hardy uses NTFS-3G by default. You didn't specify your exact error message so I can only guess, but a common problem is that if the NTFS partition is marked dirty, Linux can't mount it. The solution is to boot into Windows twice, shutting down properly both times.

the error message he said he gets, is what happens in hardy if you mount an ntfs partition using the ntfs kernel driver, i assume he was mounting manually. Also, instead of having to reboot so many times, you can use -o force in the mount paramaters to force the partition to mount, once mounted, the dirty flag is removed.

---

### Post by Oziyak on 2008-10-06
Thanks for the replies everyone.

I actually tried booting into windows and doing a proper shut down... but much to my surprise I couldnt' boot into windwos at all anymore :(   good thing I have a back up of my files.

so since that hard drive is pretty much useless to me know I'm considering doing a re-install of ubuntu as the sole OS on my PC.

thanks again for your responses

---

### Post by Kaseas on 2008-10-06
Try running ```
ntfsfix /dev/sda1
``` (replace /dev/sda1 with where your harddrive actually is,) then ```
 sudo mount force /dev/sda1
``` (or wherever you have your ntfs partition.)

---

