---
title: "Moving Ubuntu from hda5 to hda8"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by Irony on 2006-02-13
I would like to move Ubuntu from hda5 to hda8 - can I do this by simply copying the entire contents over, for example by using gksudo nautilus, or do I have to do it whilst ubuntu is unmounted for example by going to my Zenwalk installation and copying Ubuntu from hda5 to hda8?

---

### Post by GTvulse on 2006-02-13
[QUOTE=Irony]I would like to move Ubuntu from hda5 to hda8 - can I do this by simply copying the entire contents over, for example by using gksudo nautilus, or do I have to do it whilst ubuntu is unmounted for example by going to my Zenwalk installation and copying Ubuntu from hda5 to hda8?[/QUOTE]

Do it from your Zenwalk partition, or a live CD. Mount both partitions in your running linux and copy the files with rsync:
```

rsync -aS /mnt/hda5/. /mnt/hda8/.

```
Note the dots at the end of the paths, they are important.

I've moved many linux installations this way and they haven't failed me one. After you copy the files, don't forget to edit the fstab file in the new location to reflect the location and correct your grub installation and menu configuration if you plan to use boot from ubuntu's bootloader (as different from ZenWalk's).

---

### Post by Irony on 2006-02-13
Thanks dradul, that's what I was looking for.

Where you say;

[PHP]rsync -aS /mnt/hda5/. /mnt/hda8/.[/PHP]

How does linux know that /mnt is the folder to do this from, or is it creating folders called hda5 and hda8. Also is it a sudo (or su in Zenwalk) command?

---

### Post by Irony on 2006-02-13
Okay I think I see what you mean. I just create the folders call them hda5 hda8 or whatever then perform the command presumably a su command.

---

### Post by bored2k on 2006-02-13
Copy everything to your hda8 drive, then edit your /etc/fstab accordingly (hda5 --> hda8, etc) and pray it works..

---

### Post by Irony on 2006-02-13
For a while I would have 2 ubuntus, presumably I would have to reinstall grub so as to tell it to look at the new /boot/grub/menu.lst in hda8 rather than hda5?

Also is the copy command a su one?

---

### Post by bored2k on 2006-02-13
Cant you just edit the current one and change (hd0,4) for (hd0,7) or similar?

---

### Post by Irony on 2006-02-13
No 'cos I intend to delete the current one. I therefore assume that I have to somehow redirect grub to where the new root partition of ubuntu is - I think going to rescue mode with the ubuntu install cd is the way to go to do this.

---

### Post by GTvulse on 2006-02-17
[QUOTE=Irony]No 'cos I intend to delete the current one. I therefore assume that I have to somehow redirect grub to where the new root partition of ubuntu is - I think going to rescue mode with the ubuntu install cd is the way to go to do this.[/QUOTE]

Missed this one...

You don't necessarily need to use a live cd to change the grub installation. If you are installing to the MBR, you just boot into, say, the old Ubuntu and do a chroot:
```

sudo mount -t <filesystem> /dev/hda8 /mnt
sudo mount -t proc procfs /mnt/proc
sudo mount --bind /dev/ mnt/dev
sudo chroot /mnt /bin/su -

```

That chroots you in the new linux install as the super user.

Then you check your [font=monospace]/boot/grub/menu.list[/font] file to make sure that grub's root points to the new partition and that everything else is fine with the file, and then you run:
```

update-grub
grub-install /dev/hda8

```

If you are booting from grub installed in the partition's superblock, you still have to tag the new partition as the bootable one with parted, fdisk or cfdisk, whatever you find easier to use.

---

### Post by GTvulse on 2006-02-18
Do note that the example I gave above is for when you install grub in the partition superblock. ```
grub-install /dev/hda
``` is enough to install to the MBR.

---

### Post by Irony on 2006-02-25
Thanks dradul - I'm trying out the command on my Zenwalk partition first;
[PHP]
sudo rsync -aS /mnt/Zen/. /mnt/LiB/.[/PHP]

This copied the files over from hda4 to hda8, I've altered my */boot/grub/menu.lst* so I will see if I can boot into the moved version;

[PHP]
title		Zenwalk 2.01, hda4
root		(hd0,3)
kernel		/boot/vmlinuz root=/dev/hda4 ro
savedefault
boot

title		Zenwalk 2.01 moved version, hda8
root		(hd0,7)
kernel		/boot/vmlinuz root=/dev/hda8 ro
savedefault
boot[/PHP]

Next time I boot up I'll see if it works. Assuming it does how do I then delete the moved version so as to have a blank partition to copy Ubuntu to hda8 or do I have to re-format it?

---

### Post by Irony on 2006-02-26
Its worked! I booted into the moved Zenwalk in hda8 - I'll try it with Ubuntu next.

---

### Post by Irony on 2006-02-27
dradul, I've successfully moved Ubuntu, though I decided to move it from hda5 to hda3.

To point grub at the new mount point in hda3, I take it that I have to boot into the old Ubuntu in hda5 and do the following, to install grub to the MBR;

[PHP]sudo mount -t <filesystem> /dev/hda3 /mnt
sudo mount -t proc procfs /mnt/proc
sudo mount --bind /dev/ mnt/dev
sudo chroot /mnt /bin/su -
update-grub
grub-install /dev/hda[/PHP]

I would also presumably change the mount point from hda5 to hda3 in my /etc/fstab;

[PHP]/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1[/PHP]

Is that correct? Can I not just do these commands from the new Ubuntu in hda3?

---

### Post by Irony on 2006-02-28
Or should I just do on its own;

[PHP]grub-install /dev/hda[/PHP]

from the old Ubuntu in hda5.

---

