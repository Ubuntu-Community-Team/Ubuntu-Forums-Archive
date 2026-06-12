---
title: "Grub problem after HD upgrade"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by Kevin Klein on 2006-01-29
My server's hard drive recently filled up, so I replaced the old 15GB drive with a new 40GB drive.  However, I can't seem to get GRUB to work with the new drive.

First, I installed the new drive on the second IDE controller.  I partitioned it with cfdisk and formatted it with mkfs.  Then I mounted it and used rsync to copy the contents of the old drive to the new drive.  Then I used grub-floppy to create a boot floppy.  Finally, I swapped out the old drive and moved the new drive to the primary controller.

After booting from the floppy, I ran "grub-install /dev/hda1" to install grub on the new drive.

Now when I boot, I get a blank screen, it prints "GRUB" in the upper-left corner and then the system hangs.

I can boot just fine from the floppy, but I'd like to obviously eliminate the need to do so.

Any suggestions?

---

### Post by lha on 2006-01-29
[QUOTE=Kevin Klein]My server's hard drive recently filled up, so I replaced the old 15GB drive with a new 40GB drive.  However, I can't seem to get GRUB to work with the new drive.

First, I installed the new drive on the second IDE controller.  I partitioned it with cfdisk and formatted it with mkfs.  Then I mounted it and used rsync to copy the contents of the old drive to the new drive.  Then I used grub-floppy to create a boot floppy.  Finally, I swapped out the old drive and moved the new drive to the primary controller.

After booting from the floppy, I ran "grub-install /dev/hda1" to install grub on the new drive.

Now when I boot, I get a blank screen, it prints "GRUB" in the upper-left corner and then the system hangs.

I can boot just fine from the floppy, but I'd like to obviously eliminate the need to do so.

Any suggestions?[/QUOTE]

What do you have on the mbr of your 40GB drive? I guess you have remains of an old grub install there. Installing grub on mbr could help. (You do need something on mbr to load grub. It can be ms' boot code or grub's but if you use grub's, you have to tell it where the rest of boot loader is.)

---

### Post by Kevin Klein on 2006-01-29
[QUOTE=lha]What do you have on the mbr of your 40GB drive? I guess you have remains of an old grub install there. Installing grub on mbr could help. (You do need something on mbr to load grub. It can be ms' boot code or grub's but if you use grub's, you have to tell it where the rest of boot loader is.)[/QUOTE]

I thought updating the MBR was what grub-install did.

---

### Post by jjross on 2006-01-29
Check your /boot/grub/menu1st file and see if there is anything there, it should be the same as what you have on your floppy boot disk, if you have anything there, back it up, then try to copy  grub from the boot floppy to your menu 1st file. If there is nothing there that might be the problem.
[COLOR="Red"]Anyone else please feel free to correct me on this[/COLOR]

---

### Post by lha on 2006-01-30
[QUOTE=Kevin Klein]I thought updating the MBR was what grub-install did.[/QUOTE]

You said in your previous post
[QUOTE=Kevin Klein]I ran "grub-install /dev/hda1"[/QUOTE]

That puts grub on the boot sector of your first partition on 40GB. What I suggested you to try, is "grub-install /dev/hda". Notice there's no number after hda. This will install grub to mbr.

---

