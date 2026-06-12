---
title: "hibernate not working"
date: 2008-07-12
forum: General Help
---

### Post by Samrat Rao on 2008-07-12
i have ubuntu 7.10 installed in my system. i shifted the swap partition (size more than ram) to another location and changed the UUID in /etc/fstab. Hibernate stopped working and then i was told to update UUID in etc/initramfs-tools/conf.d/resume as well which i did. now the pc will hibernate partially i.e. it will not restart. whatta do?

---

### Post by prshah on 2008-07-12
> **Samrat Rao said:**
> 
 i shifted the swap partition to another location and changed the UUID in /etc/fstab. Hibernate stopped working and then i was told to update UUID in etc/initramfs-tools/conf.d/resume as well which i did. now the pc will hibernate partially i.e. it will not restart. whatta do?

Did you do ```
 sudo update-initramfs -u
``` after updating the "/etc/initramfs-tools/conf.d/resume" file ? Until then, your changes will not take effect. If you've already done this, or if it doesn't help, post/check outputs to the following commands:

1) Does swap exist```
sudo fdisk -l | grep -i swap
```
2) is it activated```
swapon -s
```
3) does ```
cat /etc/initramfs-tools/conf.d/resume
``` show the correct uuid for the swap partition as mentioned in ```
cat /etc/fstab
```
4) is the swap uuid actually correct? ```
sudo vol_id /dev/swapdev
``` Replace swapdev with the actual device as found out from fdisk. 
5) check if grub's menu.lst file contains a "resume=" directive which is pointing to a non-existent swap partition UUID.
6) glance through /usr/share/initramfs-tools/scripts/local-premount/resume script for errors

If the swap uuid in step 3 is wrong, you can change it manually, then run the "sudo update-initramfs -u" command to update the new uuid value

OR

you can give the ```
mkswap -U UUID /dev/swapdev
``` command to reinitialize the swap with the given UUID (replace /dev/swapdev with the actual reference from fdisk for the swap partition.)

Please post back outputs/errors/sucess.

---

### Post by Samrat Rao on 2008-07-13
after the hibernation problem, i had to install open suse 11, but the open suse grub didn't get installed.

here are the results of the codes mentioned above:

i did sudo update-initramfs -u before also.

root is on /dev/sda9 and presently swap is on /dev/sda7. before i changed swap location, i think swap was on /dev/sda8

RESULTS:
code: sudo fdisk -l | grep -i swap
/dev/sda7            7772        8071     2409718+  82  Linux swap / Solaris

code: swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda7                               partition       2409708 0       -1

Both 
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab
   have the same UUID

code: sudo vol_id /dev/swapdev
/dev/swapdev: error opening volume

 grub's menu.lst file does not seem to contain a "resume=" directive other than the line:
 '## e.g. defoptions=vga=791 resume=/dev/hda5'

 i have no idea about any errors in /usr/share/initramfs-tools/scripts/local-premount/resume

what do i do next?

---

### Post by prshah on 2008-07-13
> **Samrat Rao said:**
> 

Both 
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab
   have the same UUID

code: sudo vol_id /dev/swapdev
/dev/swapdev: error opening volume



1) Post here the UUIDs in the /etc.../resume file;
2) You have to replace /dev/swapdev with the actual swap device partition, in your case ```
sudo vol_id /dev/sda7
```

---

### Post by Samrat Rao on 2008-07-15
in /etc.../resume file: RESUME=UUID=d6259cf1-6b8c-479a-b216-1670249f279f

and by typing sudo blkid, the swap UUID is: UUID=d6259cf1-6b8c-479a-b216-1670249f279f

when i did sudo vol_id /dev/sda7 (swap partition), i get:
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=d6259cf1-6b8c-479a-b216-1670249f279f
ID_FS_UUID_ENC=d6259cf1-6b8c-479a-b216-1670249f279f
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

how do i replace /dev/swapdev with the actual swap device partition, in my case it is /dev/sda7.

---

### Post by prshah on 2008-07-15
> **Samrat Rao said:**
> RESUME=UUID=d6259cf1-6b8c-479a-b216-1670249f279f
the swap UUID is: UUID=d6259cf1-6b8c-479a-b216-1670249f279f
when i did sudo vol_id /dev/sda7 (swap partition), i get:
ID_FS_UUID=d6259cf1-6b8c-479a-b216-1670249f279f
ID_FS_UUID_ENC=d6259cf1-6b8c-479a-b216-1670249f279f


OK all UUIDs match, I have no idea why it's not working.

---

### Post by Samrat Rao on 2008-07-16
just in case, in my ubuntu 7.10, s2ram also never worked though hibernate worked. now after shifting swap (keeping it same size & more than ram), neither works. will this info help?

---

### Post by pcolamar on 2008-07-18
I have just followed the instruction (verified and corrected the right swap's UUID) and finally s2ram seems to work.
There is still one little problem, when it resumes my wi-fi card is not on.
Any suggestion?

I have also noted that "hibernate" does not seems to work. 
"sudo hibernate " does not do anything if not just a flicker of the screen.

Thanks

Palmer

---

