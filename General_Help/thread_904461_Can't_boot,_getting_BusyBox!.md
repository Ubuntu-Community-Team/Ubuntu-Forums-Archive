---
title: "Can't boot, getting BusyBox!"
date: 2008-08-29
forum: General Help
---

### Post by mmzdaniel on 2008-08-29
Hey, 
Me again, after the last thread in which the problem was after installing the Fingerprint usplash theme, i managed to screw something up again. Whenever I boot, I get some text on the screen and eventually it gives me BusyBox instead of Ubuntu.
It also gives me this error:
```
error while loading shared libraries: libfuse.so.2
```
I am using Wubi to mount the 64bit ubuntu.
I just did a chkdsk /r on windows but it didn't work.
Help me :(

---

### Post by ac1d6urn on 2008-08-29
Just googled for your error, and [FUSEWiki suggests the following]("http://fuse.sourceforge.net/wiki/index.php/FAQ?PHPSESSID=f96e2a8492c27ff228b9702100b6afe1#Why_is_there_an_error_loading_shared_librariesx3f."): 
[INDENT]check /etc/ld.so.conf for a line containing '/usr/local/lib'. If it's missing, add it, and run ldconfig afterwards [/INDENT]

might be worth checking... so.

1. At busybox prompt type **exit **to get back to the shell.
2. then type: **cat /etc/ld.so.conf **[enter] to check what it contains
3. if the contents say 'include filename', repeat #2 with that new filename and check for '/usr/local/lib' in it as well.

Let me know if it looks like it's missing.

---

### Post by mmzdaniel on 2008-08-29
Ok ill try it right now. be right back :O
when i type exit and hit enter, i get this:
```
mount: mounting /root on /host failed: invalid argument
```

---

### Post by Crafty Kisses on 2008-08-29
Try this: shutdown Windows XP correctly, just go to Start and logout, then try.

---

### Post by mmzdaniel on 2008-08-30
I did it before i asked help in here, i did do some research but i didnt get everything... i also tried chkdsk /r, didnt work...

---

### Post by ac1d6urn on 2008-08-30
> **mmzdaniel said:**
> Ok ill try it right now. be right back :O
when i type exit and hit enter, i get this:
```
mount: mounting /root on /host failed: invalid argument
```

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/226622/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/226622/+viewstatus)  Sounds a lot like this case.  Take a look, does the description match what you're getting?

---

### Post by mmzdaniel on 2008-08-30
pretty much, and i do get this:
Mounting... on /root failed: Success

---

### Post by ac1d6urn on 2008-08-30
> **mmzdaniel said:**
> pretty much, and i do get this:
Mounting... on /root failed: Success

Hmm. If you try to boot to windows, does it start as usual or try to go through a check disk/give you any messages?  (Make sure to let it boot to desktop and shutdown from the start menu afterwards.)

---

### Post by mmzdaniel on 2008-08-30
Everything's normal, and i already did a chkdsk /r...
i defragment my drive every week, i clean all the trash M$ leaves including cookies, i do a virus scan every day... my PC is for gaming, i have it in tip top condition. ill try shutting down again though.
also when i type this in busybox:
```
mount /root on /host
```
i get this:
```
mount: cannot read /etc/fstab: no such file or directory
```

---

### Post by mmzdaniel on 2008-08-31
Bump

---

### Post by mmzdaniel on 2008-09-02
Last time ill say this, Bump :(

---

