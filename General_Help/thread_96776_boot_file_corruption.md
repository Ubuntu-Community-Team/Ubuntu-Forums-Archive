---
title: "boot file corruption"
date: 2005-11-29
forum: General Help
---

### Post by bigpup on 2005-11-29
I need some advice on how to proceed.
Boot failed yesterday with this message:

Unexpected inconsistency; run fsck manually
(i.e. without -a or -p options)
fsck failed. Please repair manually and reboot. Please note that the root file system is currently mounted read-only. To remount it read-write:
# mount -n -o remount,rw /
CONTROL-D will exit from this shell and reboot.
bash: lesspipe: command not found
bash: dir colors: command not found
root @ (none): ~#

After remounting root fs, fsck warns me that it can do damage on a mounted volume. When I do run fsck it fails.

I tried reinstalling Ubuntu from CD, but I'm intimidated by Partition Manager. I have:
Primary #1 = Windows 2000
Primary #2 = 5.4 GB Ubuntu
Logical#5 = 658 MB Swap
Logical #6 = 13.9 GB FAT 32

I don't want to lose the FAT 32, which is shared with W2K, so I backed out of the installation. Then GRUB is hosed, so I cannot boot W2K, either.

How to fix the corrupted files (e.g. from Live CD), or how to reinstall with least messing around on partitions. How to restore, or temporarily replace, GRUB?

---

### Post by Robgould on 2005-11-29
what did you change before you had the boot failure?  I believe you can use the install CD to boot in rescue mode, but you need to know what to undo when you get there.  I am not an expert, just telling you what I believe.  If you can make a list of things you did that you think might have broken the system, you can ask use the disk to boot and try to repair them.

---

### Post by Robgould on 2005-11-29
To boot to windows.....
 
use windows install disk.  Got to recovery console.  Run fixmbr or fdisk /mbr.  The command is different depending on your version.  This will allow windows to boot.  It will remove grub.  You will have to re-install grub.

---

### Post by bigpup on 2005-11-29
I did not change anything. The last time I booted, I probably got Ubuntu updates, but I did not mess with anything myself.

---

### Post by Robgould on 2005-11-29
If it were me...I would repair my mbr so that I could boot to windows.  I am more confident there.  I would use windows to repartition hard drive.  I would then re-install Ubuntu to free space I created.  Just my opinion.

---

### Post by bigpup on 2005-11-29
Thanks. I used fixmbr, and Windows is back in business. I'll take care of Ubuntu later, when I don't have a load of work to do.

---

### Post by tomski on 2005-11-29
boot up in resue mode via the live cd (get it in win if you ain't got it), follow the questions the same way when you installed ubuntu,when asked for password or ctrl-d give a password for a console and type :

$ cat /boot/grub/menu.lst

and check that this is pointing to the correct partitions and files if not edit with an editor :

$ nano(or vi/vim) /boot/grub/menu.lst

and edit so it is correct, then type :

$ grub-install /dev/hda

you can ignore the errors about xfs (unless you use this)

then if you still have one create a boot floppy with :

$ grub-install /dev/fd0

then when this is all done you will know next time round what to do and you have created 3 options grub floppy/win cd/live ubuntu cd

---

