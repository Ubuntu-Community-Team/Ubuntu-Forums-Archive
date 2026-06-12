---
title: "Problems mounting external hard disk after latest kernal update"
date: 2008-10-17
forum: Hardware
---

### Post by Mojomagus on 2008-10-17
Hi all,

Been searching the forum for an answer to this but haven't quite managed to find one.

I have I 500GB (FAT32) external hard disk that was working beautifully until two days ago when I was prompted to upgrade to the new kernel version. 

Before Ubuntu would mount the hard disk every time i switched it on. Now when I turn it on nothing happens. If I got to places it does not appear, its like its not even connected. The only way I can get it to work is if I restart with the hard disk on, but if I dismount it, its gone again and can't get it back.

Any ideas on this? I would really appreciate the help.

---

### Post by vanadium on 2008-10-17
Try booting with a previous kernel to see whether the issue persists. If not, then you should probably use your old kernel in the mean time and await the next update.

---

### Post by Mojomagus on 2008-10-17
Hey! thanks for the reply.

I tried manually booting with a previous version kernel as you suggested (2.6.24-19 instead of 2.6.24-21) and indeed things where back to normal. 

So, if there is no other solution I guess I can always boot 2.6.24-19 for things to be stable. But how do I configure Ubuntu to run this older version of the kernel automatically? Also, should I not file a bug report somewhere?

---

### Post by vanadium on 2008-10-17
To boot your previous kernel by default, open the file /boot/grub/menu.lst (gksudo gedit /boot/grub/menu.lst). Find the lines after ## ## End Default Options ##:

```

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=c9cb8b29-152a-47ac-b952-5b9909a290ba ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

...

```
Add a comment sign (#) before any line of the paragraphs "kernel 2.6.24-21-generic" and "Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)". Save the file.

Obviously you should file the bug if you can do that. Check first if it has not already been filed.

---

### Post by Mojomagus on 2008-10-17
Thanks, I'll try that with the kernel.

As for filling the bug I'll see if I can figure out how to do that.

---

