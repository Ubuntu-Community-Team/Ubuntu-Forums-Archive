---
title: "Want to create a Windows Partition"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by source.decay on 2009-04-30
Hi,

I am happily using Ubuntu on my HP dv6000 Laptop, but I need to use a program that will only work on Windows.  I have devoted my entire hard drive to Ubuntu and now I would like to set up a partition for Windows, but I cannot figure out how to do this without deleting my entire hard drive.

Is there a way to do this without making me want to pull my hair out?

Thank you!

---

### Post by Sef on 2009-04-30
What program do you want to run?   It may work with WINE.

If it doesn't, then you can create a partition for Windows.   However, Windows needs to be installed on the first primary partition.  I will post more when i have the time and can find some more information, unless someone else posts it first.

---

### Post by illieas19 on 2009-04-30
Try EASUS Partition master to set up separate partitions for both Windows and the Swap Partition.

---

### Post by source.decay on 2009-05-01
> **Sef said:**
> What program do you want to run?   It may work with WINE.

If it doesn't, then you can create a partition for Windows.   However, Windows needs to be installed on the first primary partition.  I will post more when i have the time and can find some more information, unless someone else posts it first.

I'm trying to run LabVIEW.  I have tried running it on Ubuntu, but the modules that I use do not run on Linux or Wine.

I thought that I might have to erase my hard drive first and install Windows first and then put Ubuntu back on, but I was hoping to avoid doing that if possible.

Thank you for any help you can offer.

---

### Post by jakupl on 2009-05-01
download the super [grub live cd]("http://forjamari.linex.org/frs/download.php/1138/super_grub_disk_0.9783.iso") and burn it as an image.

boot into the ubuntu live cd, and resize the ubuntu partition. Just leave the free space.

install windows to the unpartitioned space.

now you will find that you can't boot into ubuntu, this is because windows has replaced grub with its own bull*%&#.
Boot the supergrub and restore grub from there.

go into ubuntu, now you probably can't boot into windows, you will need to add windows to /boot/grub/menu.lst. here are instructions on how to do that. [http://www.linuxforums.org/forum/ubuntu-help/68350-add-windows-grub.html](http://www.linuxforums.org/forum/ubuntu-help/68350-add-windows-grub.html)

---

### Post by source.decay on 2009-05-01
> **illieas19 said:**
> Try EASUS Partition master to set up separate partitions for both Windows and the Swap Partition.

Hmm, that looks like a great programme.  However, it will not run through WINE.  Thank you for the suggestion.

---

### Post by source.decay on 2009-05-01
> **jakupl said:**
> download the super [grub live cd]("http://forjamari.linex.org/frs/download.php/1138/super_grub_disk_0.9783.iso") and burn it as an image.

boot into the ubuntu live cd, and resize the ubuntu partition. Just leave the free space.

install windows to the unpartitioned space.

now you will find that you can't boot into ubuntu, this is because windows has replaced grub with its own bull*%&#.
Boot the supergrub and restore grub from there.

go into ubuntu, now you probably can't boot into windows, you will need to add windows to /boot/grub/menu.lst. here are instructions on how to do that. [http://www.linuxforums.org/forum/ubuntu-help/68350-add-windows-grub.html](http://www.linuxforums.org/forum/ubuntu-help/68350-add-windows-grub.html)

Thank you!  I'm going to try that now.

---

### Post by jakupl on 2009-05-01
well that last link that I gave you was not that good... but I have done it before, so it should not be that difficult.

---

