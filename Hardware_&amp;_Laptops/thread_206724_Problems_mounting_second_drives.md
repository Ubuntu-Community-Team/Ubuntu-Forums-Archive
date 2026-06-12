---
title: "Problems mounting second drives"
date: 2006-06-30
forum: Hardware &amp; Laptops
---

### Post by V0oD0oman on 2006-06-30
I've got an ubuntu server setup with 3 different mirrored raid drives, all formatted in JFS.  Our power cables fell out during the upgrade to 6.06 and we had to re-install the OS.  Now ubuntu is back to normal, however my two drives that stored only data will not mount for me.  Under gparted it shows they are JFS, however when I go to disk utilities, it says "unknown" for the filesystem and will not let me mount.  I manually edited /etc/fstab to include these drives to mount them, and when I do **sudo mount -a** it gives me the following error.

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Now I know that these drives are still working fine, because I booted with a Knoppix livecd and the drives auto mount on boot and work fine.  I am currently backing up the data via knoppix (slow slow slow!), but what I really want to do is re-mount the two drives in ubuntu and start sharing them on the domain once again.  Can anyone point me in the right direction?

---

### Post by woedend on 2006-06-30
did you double check your fstab to make sure everything was written/spelled correctly?
Ive only seen that error when I had misspelled the filesystem type(IE I put fat instead of vfat)

---

### Post by dannyboy79 on 2006-07-25
What do you get when you do what it suggests? dmesg | tail? Post those results and we can maybe help further.

---

### Post by unimind on 2006-07-27
I have the same problem with a couple of jfs formated drives on my server.  They worked fine under ubuntu 5.10 and after installing 6.06 LTS, they are not recongized (unknown format).

I was searching arounfd and found this thread that seemed to help... [http://www.ubuntuforums.org/showthread.php?t=209345&highlight=jfs](http://www.ubuntuforums.org/showthread.php?t=209345&highlight=jfs) 
Hope it works for you.

---

