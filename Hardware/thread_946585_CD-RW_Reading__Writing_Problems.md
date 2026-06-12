---
title: "CD-RW Reading / Writing Problems"
date: 2008-10-13
forum: Hardware
---

### Post by condeh on 2008-10-13
Hi to all,

Currently using Hardy, switched from Etch for a change a few months ago. Have run across a problem that i had once upon a time with etch,but was rectified.
Basically, my cdrw drive can write cd-r(w) fine, as in, the disk physically looks like it has been written, and no matter what program i use to do the writing, no error messages are given. by all accounts, a 100% ok writing process.
However, removing the cd and then putting it back in, to be read, results in the following dmesg output
```
[ 5812.403374] cdrom: This disc doesn't have any tracks I recognize!

```
This occurs with all cd-r(w)s written with this laptop, including others which have previously worked.

So, essentially, I cannot read or write writeable cds. I can read normal cds and dvds fine.

My memory is a bit rusty, but in etch, this problem was intermitent, but required a "hdparm -w /dev/hdc" (as it was on etch). however, trying the same here results in the following.

```
john@XubLap:~$ hdparm -w /dev/cdrom

/dev/cdrom:
 resetting drive
 HDIO_DRIVE_RESET failed: Inappropriate ioctl for device

```

I would really appreciate any input.

This is an Acer Aspire 9301, the CD drive is an Optiarc DVD RW AD-7530A,

thanks,
John.

---

### Post by cariboo on 2008-10-13
Try running your command this way:

```
sudo hdparm -w /dev/cdrom
```

Jim

---

### Post by condeh on 2008-10-13
Hi, thanks for the reply.

I have tried it as root, with the same result. I did it again as myself just to get the exact error for my original post.

John.

---

### Post by condeh on 2008-10-18
bump?

---

### Post by ajkain on 2008-10-29
Same problem: I cannot read CD-RWs but I write them, damn!!! :(
Do you find a solution?

---

### Post by condeh on 2008-10-29
I still have a debian etch partition, so I switch to that if I need to. Its a ridiculous situation, but have found no way of rectifying the problem in ubuntu.

---

### Post by ajkain on 2008-10-29
Is it a bug?
I'm looking for it on Launchpad but I'm finding nothing.

---

