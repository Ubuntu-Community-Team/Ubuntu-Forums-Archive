---
title: "Mount NTFS external hard drive?"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by BennieBlount on 2008-02-04
I am using Ubuntu 7.10   I don't have a Windows computer but I do have an external hard drive formated in NTFS - it contains files from my previous Windows system. I want to extract the files from the external hard drive but I get a "Cannot mount" error.

Before settling with Ubuntu I tried other Linux versions (PCLinux, Open Suse, Freespire, etc) and was able to mount my external hard drive.

The details from the error message says that I can do this:

   mount -t ntfs-3g /dev/sdb1 /media/disk -o force

When I try that the terminal tells me I need to be "root" , but it does not tell me how to be "root"

1. How do I become "root"

2. Is there another way to mount this NTFS formated hard drive in Ubuntu 7.10?

Thanks,

Bennie

---

### Post by chrisdeckard on 2008-02-04
Prepend "sudo" to the command.

-Chris

---

### Post by vanadium on 2008-02-04
This is a frequent question. Ubuntu will not mount an ntfs volume that is "unclean", i.e. it has not been properly disconnected at some time. The solution to this is to repair the file system. Unfortunately, this can only be done with a Windows system, which is why you shoudl avoid using ntfs if you do not have Windows. I am not suer wether the Linux checking tool, ntfsfix, is sufficient to "fix" the disk allowing it to mount automatically.

However, as you have seen from the error message, there is an emergency solution if you do not have Windows, and that is to "force" mounting. This should be considered an emergency solution, though, as it is on your own risk: if you continue to read and write on a force mounted disk, you risk to corrupt the disk further. You can use the "force" option if you intend to mount the disk in order to copy the data elsewhere, after which you eventually can reformat the disk.

That said, here is how you "force" mount the disk for reading:

sudo mkdir /media/disk
sudo mount -t ntfs /dev/sdb1 /media/disk -o force

Change ntfs to ntfs-3g if you want to write, but I strongly recommend against that for a forced mount.

With "sudo", you are acting as root.

---

### Post by elope on 2008-04-18
I had the same problem mounting a NTFS drive. Not a good friend of Gates and Balmer, I decided to live a little. 

By running NTFSFIX from the terminal with the following command, where sda1 is my external NTFS drive the problem was solved.

[INDENT]ntfsfix /dev/sda1[/INDENT]

After the fix I simply mounted the drive by clicking on Places > Computer > "name of my drive"

Rock on and thanks for the tip.

---

### Post by putsgetsname on 2008-05-22
Yes,same problem.
My ntfs external hard drive would not mount "unclean".
I had connected/disconnected it to my windows computer a lot with the o/s running.
On the ubuntu machine, i tried to get it to mount automaticaly,then tried to force it to mount with the same result "cannot mount" "unclean" error, I gave up,plugged it back into the windows computer to test it.It loaded/mounted itself and showed its contents fine.
I used the "safely remove hardware" option to disconnect this time,and re    tried with the ubuntu machine.
Problem solved for me.

---

