---
title: "fstab Mounting Issues"
date: 2010-01-24
forum: Hardware
---

### Post by lives4him06 on 2010-01-24
Hello!
I am having trouble mounting an external disk using fstab. I have the disk (/dev/sdc1) formatted to ext2.

The disk mount fine manually using the command:
```

sudo mount -t auto /dev/sdc1 /media/usbDrive/

```

However, when I go to use fstab using the line:

```
/dev/sdc1 /media/usbDrive ext2 rw,user,auto,utf8 0 0

```

I get the following error:

```

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Here's proof that the file system is ext2:

```
jeff@jeff-desktop:~$ sudo file -s /dev/sdc1
/dev/sdc1: Linux rev 1.0 ext2 filesystem data, UUID=1f5499f8-3109-46b8-8043-efead0e53bb5, volume name "BigStorage" (large files)
```

What am I doing wrong?

---

### Post by dE_logics on 2010-01-24
How bout changing rw,user,auto,utf8 to 'defaults'?

I bet that utf8 is causing problems.

---

### Post by lives4him06 on 2010-01-24
Wow, thanks for the speedy response. Thanks a bunch! That was the problem.

Now, I'd like to mount this device on start up for all users rwx. How do I do that?

---

