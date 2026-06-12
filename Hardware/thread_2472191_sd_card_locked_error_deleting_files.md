---
title: "sd card locked error deleting files"
date: 2022-02-20
forum: Hardware
---

### Post by loudi on 2022-02-20
Hi
I couldn't see the option to delete files from my sd card when right-clicked on it. I couldn't change permissions either (and i notice that I can't change permissions on my USB drive either). I removed the sd card adapter to verify that it was not physically locked, and when I reinserted it, it doesn't show in nautilus anymore.

blkid gives:
```
ludi@ludi-ThinkPad-T430:~$ blkid
/dev/mmcblk0p1: LABEL_FATBOOT="Loudi" LABEL="Loudi" UUID="0030-5B4A" TYPE="vfat"
/dev/sda1: UUID="1e25178f-364d-475a-9852-45dd1fcd57ae" TYPE="ext4" PARTUUID="7b7d271a-01"
/dev/sdb1: LABEL="USB DISK" UUID="BE0B-01B3" TYPE="vfat" PARTUUID="e85a4a66-01"
/dev/loop0: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop27: TYPE="squashfs"
/dev/loop28: TYPE="squashfs"
/dev/loop29: TYPE="squashfs"
/dev/loop30: TYPE="squashfs"
/dev/loop31: TYPE="squashfs"
/dev/loop32: TYPE="squashfs"
/dev/loop33: TYPE="squashfs"
/dev/loop34: TYPE="squashfs"
/dev/loop35: TYPE="squashfs"
/dev/loop36: TYPE="squashfs"
/dev/loop37: TYPE="squashfs"
/dev/loop38: TYPE="squashfs"
/dev/loop39: TYPE="squashfs"
/dev/loop40: TYPE="squashfs"
/dev/loop41: TYPE="squashfs"
ludi@ludi-ThinkPad-T430:~$ 


```

I believe the drive in question is the first one, called "Loudi" because that's how the sd card's partition was called.

But when I do ls -la /dev/sd* before and after inserting the card, there is no extra partition showing:
ludi@ludi-ThinkPad-T430:~$ ls -la /dev/sd*
brw-rw---- 1 root disk 8,  0 févr. 20 19:12 /dev/sda
brw-rw---- 1 root disk 8,  1 févr. 20 19:12 /dev/sda1
brw-rw---- 1 root disk 8, 16 févr. 20 19:12 /dev/sdb
brw-rw---- 1 root disk 8, 17 févr. 20 19:12 /dev/sdb1
ludi@ludi-ThinkPad-T430:~$ ls -la /dev/sd*
brw-rw---- 1 root disk 8,  0 févr. 20 19:12 /dev/sda
brw-rw---- 1 root disk 8,  1 févr. 20 19:12 /dev/sda1
brw-rw---- 1 root disk 8, 16 févr. 20 19:12 /dev/sdb
brw-rw---- 1 root disk 8, 17 févr. 20 19:12 /dev/sdb1

But when I open Gparted, I do see a /dev/mmcblk0p1 partition that is called Loudi and says that the status is "mounted at /media/ludi/Loudi"
It has a key symbol next to the name of the partition.

What can I do in order to access the files in it again through Nautilus?

Thanks
Rod

Update: I see the sd card again i Nautilus. I get an error message when trying to change permissions and I still don't have the option to delete files.

Another update that might help:
When I do 'sudo nautilus' i get:
```
** (org.gnome.Nautilus:4408): WARNING **: 19:46:54.515: Unable to get contents of the bookmarks file: Erreur lors de l’ouverture du fichier /root/.gtk-bookmarks : No such file or directory

** (org.gnome.Nautilus:4408): WARNING **: 19:46:54.516: Unable to get contents of the bookmarks file: Erreur lors de l’ouverture du fichier /root/.gtk-bookmarks : No such file or directory
Nautilus-Share-Message: 19:46:54.638: Called "net usershare info" but it failed: L’exécution du processus fils « net » a échoué (No such file or directory)
```

---

### Post by Holger_Gehrke on 2022-02-20
Might be a damaged file system on the card. If the kernel detects errors in a file system it automatically gets (re-)mounted read only. Unmount the filesystem and run fsck (**f**ile **s**ystem **c**hec**k**) on it. Alternatively you can use gparted to do the check.

Holger

---

### Post by loudi on 2022-02-20
Hi Holger. Thanks!

I unmounted it and applying the fsck with ```
 sudo fsck /dev/mmcblk0p1
``` and got:
```
 fsck de util-linux 2.34
fsck.fat 4.1 (2017-01-24)
open: Système de fichiers accessible en lecture seulement
```
Which means: file system accessible as read only

If I use sudo, how come it doesn't give me permission?

UPDATE: I got the same message on the report from Gparted when trying to verify the disk through it.

---

### Post by Autodave on 2022-02-20
Does your SD card have a little switch on the side to prevent it from being written to or deleted from?  Most of mine do.

---

### Post by Holger_Gehrke on 2022-02-20
If the block device goes read only, then the card is quite probably broken. Flash memory can only be written to a certain number of times before it breaks. After a certain device specific number of write errors the controller on the card won't accept any more writes.

Holger

---

### Post by TheFu on 2022-02-20
```
sudo nautilus
```
That's the problem.  Don't do that.

---

### Post by loudi on 2022-02-20
> **Autodave said:**
> Does your SD card have a little switch on the side to prevent it from being written to or deleted from?  Most of mine do.

yes. I changed the switch and nothing changed in the hability to delete the files.

---

### Post by loudi on 2022-02-20
I tried to format it after having copied the files to another disk. I using Gparted and it worked. I copied a file into the sd card to test it. But when right-click "eject" I got an error message:
"Commandline 'eject' exited with non-zero exit status 1;
stdout: not an sg dvice or an old sg driver"

Maybe it is really broken.

---

### Post by loudi on 2022-02-20
> **TheFu said:**
> ```
sudo nautilus
```
That's the problem.  Don't do that.

Found an article explaining why. Thanks for the heads up!

---

