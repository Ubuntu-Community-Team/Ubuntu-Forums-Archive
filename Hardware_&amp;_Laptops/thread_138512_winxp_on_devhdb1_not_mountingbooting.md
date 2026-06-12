---
title: "winxp on /dev/hdb1 not mounting/booting"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by b0re on 2006-03-02
Here is my problem.. I have ubuntu on /dev/hda1 & winxp on /dev/hdb1 I cannot mount or boot winxp. grub didn't auto-add it to the menu, and I can't find any docs on howto add winxp to the menu.lst file when it's on anything other than /dev/hda1.. So I guess my question is basically this, can anybody help me add the correct lines to my menu.lst? Here's some info that might or might not help..

root@nefarious:~# update-grub
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.16-rc5-nefarious
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


root@nefarious:~# fdisk -l

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4866    39086113+   5  Extended
/dev/hda5               1          93      746959+  82  Linux swap / Solaris
/dev/hda6              94        4866    38339091   83  Linux

Disk /dev/hdb: 20.4 GB, 20419854336 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2481    19928601    7  HPFS/NTFS




root@nefarious:~# mount
/dev/hda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)


root@nefarious:~# mount -t ntfs /dev/hdb1 /mnt/winxp/
mount: /dev/hdb1 already mounted or /mnt/winxp/ busy

root@nefarious:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6              36G   15G   20G  44% /
tmpfs                 189M     0  189M   0% /dev/shm


Thanks for any help.

---

### Post by nhaines on 2006-03-02
Mounting should be simple, provided you follow the instructions in the Ubuntu Starter Guide and simply substitute /dev/hdb1 for /dev/hda1!  :)

As for GRUB, try running 'sudo gedit /boot/grub/menu.lst' and adding the following to the end of the file:

-- BEGIN PASTE --
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry added by the Ubuntu user for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
chainloader	+1

--END PASTE--

---

### Post by b0re on 2006-03-02
Thanks for the reply.. but I don't think you read my post.. My winxp is NOT on /dev/hda1 .. It is, in fact on /dev/hdb1. Also, I just realized part of this is probably a stupid kernel compiling error on my part.. Under the regular Ubuntu kernel 2.6.12-10-386 my drive mounts fine.. with my updated 2.6.16-rc5 it does not. However, that still doesn't solve my little grub issue. So here is what I have in my menu.lst for winxp currently.. Any thoughts?

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1


With Windows XP being on /dev/hdb1 ..I do need to remap grub right? Am I doing something wrong? Thanks.

---

### Post by nhaines on 2006-03-02
With all due respect, I did read your post.  That's why all my references to your Windows drive is /dev/hdb.  If you cannot mount /dev/hdb1, I would suspect that you didn't compile your kernel with the ntfs module correctly.  I usually leave well enough alone and use the default kernel images, since if you recompile the kernel you also have to recompile all modules.

As far as GRUB goes, I think you shouldn't need the map commands with Windows 2000 or Windows XP.  This is important for DOS, but Windows XP assigns drive letters by serial number, so even if you move your harddrives around, if you boot Windows, it still sees its original drive as drive C.

Try this:

title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

---

