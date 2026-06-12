---
title: "Problems mounting external drives"
date: 2010-10-05
forum: Hardware
---

### Post by Zappus on 2010-10-05
Hello there!

I have faced a problem today, whenever i insert and external drive into my machine it gives me an error.

"Unable to mount 8.2 GB Filesystem
Error creating moint point: No such file or directory"

I have tried almost everything i can think of but nothing seems to work. 

Any ideas what is going on? I really have no interest in reinstalling ubuntu over again :P

---

### Post by dabl on 2010-10-05
The usual mount point for external drives is under /media. Can you take a look at /media/ and see if there are a lot of directories there, that look like /media/disk-1, /media/disk-2, etc.?

Also, when you remove an external USB disk, do you normally unmount it (or use "eject" or "safely remove" in the file manager)?

---

### Post by Zappus on 2010-10-05
Where exactly is the /media/ located?

And yes i always use the safe remove before removing the drive.

---

### Post by luvshines on 2010-10-05
/media is placed in / ie Root :)

Place->Computer->Filesystem->Media

---

### Post by spiky001 on 2010-10-05
or from terminal ```
cd /media && ls
``` post output

---

### Post by Zappus on 2010-10-05
after entering "cd /media && ls" result is 

"bash: cd: /media: No such file or directory"

---

### Post by spiky001 on 2010-10-05
thats a small (L) ls looks like you used i

---

### Post by dabl on 2010-10-05
> **Zappus said:**
> 

"bash: cd: /media: No such file or directory"

That would do it.  :(

However, /media is a standard Linux filesystem directory -- it shouldn't just disappear in the night.  Have you had any problems, or made any attempts to change your system, that might have cause a top-level directory to be removed, or moved?

---

### Post by Zappus on 2010-10-05
Well i installed VirtualBox a day ago and some virtual machines on it, other than that i had no changes that i wouldn't normally do. Is this problem fixable?

---

### Post by dabl on 2010-10-05
Yes, it can be fixed.  But before fixing, let's be 100% certain about the problem.  In the terminal window, please 

```
cd /
```

then

```
ls -l
```

and post the output.

---

### Post by Zappus on 2010-10-05
total 116
drwxr-xr-x   2 root root  4096 2010-09-21 01:11 bin
drwxr-xr-x   3 root root  4096 2010-09-28 16:29 boot
drwxr-xr-x   2 root root  4096 2010-09-10 17:09 cdrom
drwxr-xr-x  18 root root  3860 2010-10-05 22:10 dev
drwxr-xr-x 155 root root 12288 2010-10-05 21:29 etc
-rw-r--r--   1 root root 21645 2010-09-10 18:53 getskype-linux-bet-a-ubuntu-32
drwxr-xr-x   3 root root  4096 2010-09-10 17:09 home
lrwxrwxrwx   1 root root    33 2010-09-28 16:29 initrd.img -> boot/initrd.img-2.6.32-25-generic
lrwxrwxrwx   1 root root    33 2010-09-10 17:48 initrd.img.old -> boot/initrd.img-2.6.32-24-generic
drwxr-xr-x  20 root root 12288 2010-09-22 08:34 lib
drwx------   2 root root 16384 2010-09-10 17:00 lost+found
drwxr-xr-x   2 root root  4096 2010-04-23 12:11 mnt
drwxr-xr-x   4 root root  4096 2010-09-11 23:47 opt
dr-xr-xr-x 197 root root     0 2010-10-05 14:23 proc
drwx------  14 root root  4096 2010-10-05 22:24 root
drwxr-xr-x   2 root root  4096 2010-09-21 01:11 sbin
drwxr-xr-x   2 root root  4096 2009-12-05 22:55 selinux
drwxr-xr-x   3 root root  4096 2010-09-10 18:23 srv
-rw-r--r--   1 root root     0 2010-09-11 00:14 sslstrip.log
drwxr-xr-x  12 root root     0 2010-10-05 14:23 sys
drwxrwxrwt  18 root root  4096 2010-10-05 22:35 tmp
drwxr-xr-x  11 root root  4096 2010-09-10 18:22 usr
drwxr-xr-x  15 root root  4096 2010-04-29 14:26 var
lrwxrwxrwx   1 root root    30 2010-09-28 16:29 vmlinuz -> boot/vmlinuz-2.6.32-25-generic
lrwxrwxrwx   1 root root    30 2010-09-10 17:48 vmlinuz.old -> boot/vmlinuz-2.6.32-24-generic

---

### Post by dabl on 2010-10-05
Strange.  But true.

OK, while you are still at the "/" directory,

```
sudo mkdir -p media
```

then ```
ls
``` and make sure there is now a /media directory.

---

### Post by Zappus on 2010-10-05
yep, now the media folder is there, further steps?

edit: oh now the usb drive works perfectly! 

Thanks alot for the help!

---

### Post by dabl on 2010-10-05
> **Zappus said:**
> 

edit: oh now the usb drive works perfectly! 

Thanks alot for the help!

Cool.

Beware of any operation as "sudo" that might delete the /media directory -- as you can see, it is very useful.  :guitar:

---

