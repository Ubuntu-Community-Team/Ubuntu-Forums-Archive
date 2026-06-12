---
title: "BIG Mounting problems: Please Help Me!!!"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by Epperly on 2006-08-29
I have two hard drives and my primary has windows my slave has Ubuntu. My primary is mounted by ntfs-fuse but every once in a while I'll go on Windows to use like Photoshop or something.
But, everytime I go on windows for a little and my Ubuntu HD takes a break, when I come back onto Ubuntu my Windows HD gets unmounted, meaning I have to go back to Windows to do a scandisk.

Well, I did that and when I restarted into Ubuntu it didn't work, so I go back to Windows but I get this really long blue-screen-of-death error, and if my HD died AGAIN, I'm gonna be pissed because this is my 2nd hard drive from Dell.

**I HAVE ATTATCHED THE B.S.O.D. ERROR**

PLEASE HELP!!!
I hate Windows so much I wish there wasn't shit on there I sometimes need to use. :(

---

### Post by bernied on 2006-08-29
> But, everytime I go on windows for a little and my Ubuntu HD takes a break, when I come back onto Ubuntu my Windows HD gets unmounted, meaning I have to go back to Windows to do a scandisk.
Can you clarify this? What do you mean by unmounted? What is the error you get, if any, in ubuntu?

Also can you post the results of the following (from ubuntu):
cat /boot/grub/menu.lst
sudo fdisk -l
cat /etc/fstab
mount

If this is not possible, can you boot to a live-cd?

---

### Post by Epperly on 2006-08-29
When I say unmounted I meant like I can't access it or view anything in it. And the shortcut on the desktop for it goes away.

Uploaded results.txt to what you told me to do.
I can boot to a liveCD, yea why do you ask that though?

---

### Post by bernied on 2006-08-29
I only asked if you could run a live cd in case your ubuntu wasn't working.

My understanding is that access to ntfs filesystems in linux is fairly new, and not always safe or reliable. I guess yours is one of those cases - that ntfs-fuse may be messing with the filesystem. So do you really have to share that windows partition with ubuntu?

I'd suggest changing the line in /etc/fstab that starts with /dev/hdc2 so that it includes the ro option, like this:
```
/dev/hdc2      /windows    ntfs-fuse    auto,gid=1002,umask=0002,ro    0    0
```this will make it mount that partition read-only - you won't be able to change any of the files. If this fails, you could just remove the line. But then you would not have any access to the partition, which I guess you don't want.

The usual strategy for dual-booters is to have a shared partition, generally with FAT32 filesystem - this is easily accessible from both linux and windows. This partition will look like another disk drive to windows.

---

### Post by Epperly on 2006-08-29
Thank you! I can access that HD now and my stuff's still there, but I can't get on Windows still I get the BSOD error still. Oh well, so long as I can backup my 4,000 songs I'm happy :)

Now to just find a program to backup them.
Thanks.

---

### Post by bernied on 2006-08-29
Have you tried a windows recovery cd?

---

### Post by Epperly on 2006-08-29
Nope I don't think I really know how to use it, hah.. if I can find where the CD is in the first place :p

---

