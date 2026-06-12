---
title: "Hard drive clone"
date: 2015-08-08
forum: Hardware
---

### Post by oierlauzi-r on 2015-08-08
Hello! 
I'm planning to downgrade my server's main SSD (120GB) to a 60GB SSD so I can use the 120GB SSD in my Steambox. For doing it I'm using dd but aparently doesnt copy all the files, so I can't boot from the new SSD. (obviusly I'm  using less than 60GB in my hard drive, about 20GB) I think that some files are fragmented in the end of the disk and dd is only copying the first 60GB, no matter if there is something written or not. Is there anyway to solve this?
Thank you and sorry for my bat English.

P.D: This the command I'm using: dd if=/dev/sdb of=/dev/sda bs=4M

---

### Post by mikewhatever on 2015-08-08
Writing 120GB to 60GB with dd is not going to work, as it cares nothing about how much space you use. dd copies it all, used and unused, and filesystem blocks.
Try fsarchiver for copying just the used ones.

---

### Post by oierlauzi-r on 2015-08-08
fsarchiver doesn't allow to copy a hard drive, just partitions

---

### Post by wirywolf on 2015-08-08
Are you planning to put your games on a HDD? I would use the 60GB SSD in the Steam Machine. 120GB is too small to put a bunch of large games on it.

---

### Post by oierlauzi-r on 2015-08-08
Im planning to put some games in a HDD and others in the SSD, depending how often do I play them

---

### Post by wirywolf on 2015-08-08
Ubuntu Community Help Wiki - [rsync]("https://help.ubuntu.com/community/rsync")
ArchWiki - [rsync]("https://wiki.archlinux.org/index.php/Rsync")

Use them with caution! You can or will destroy personal data. You might want to consider starting fresh.

---

### Post by weatherman2 on 2015-08-08
One way to do it: boot a live USB of Linux with Gparted on it (e.g. Ubuntu), shrink your old partition to be able to fit on the new SSD.  Then use Gparted to copy the partitions (it has a copy and paste capability).    Don't copy your swap - just make a new one.

You may need to edit the /etc/fstab file of the new SSD's root partition in case the UUIDs changed.  Type this:

```
sudo blkid
```

and see if the UUIDs of your new SSD changed (swap did for sure).  Update the UUIDs in your /etc/fstab if necessary.

Once these are complete, install/update Grub on the new SSD (power down and disconnect the old SSD after the last steps but before updating Grub, then boot the live USB again.)  I prefer the chroot method of updating Grub - do a web search for "ubuntu grub chroot" and follow the instructions, only a few commands you can copy and paste, and this should be quick.

---

### Post by oierlauzi-r on 2015-08-21
I have solved using gpared, I have changed partitions size like a worm an then leave a 60GB empty space at the end. After that dd is working

---

