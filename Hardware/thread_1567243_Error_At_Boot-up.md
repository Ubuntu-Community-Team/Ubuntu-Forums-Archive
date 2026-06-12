---
title: "Error At Boot-up"
date: 2010-09-03
forum: Hardware
---

### Post by calmblythe on 2010-09-03
Hey, guys.
After installing some updates and rebooting into 32-bit Ubuntu (PAE), I continuously get this message:

```
ALERT! /dev/disk/by-uuid/bbc9999d-4587-4471-93cd-958dacd01a87 does not exist. Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)_
```

Does anyone know why this keeps happening? I can boot into the non-PAE part just fine, but I want my 4.0GB of RAM and my visual effects back (and whatever else is missing that I haven't noticed as yet).

---

### Post by quixote on 2010-09-05
(Erm, ... what's "PAE"?)

What's happened is the grub bootloader has lost track of where that operating system is, so it's falling back to a superminimal, pre-boot OS called Busybox on the assumption that then you can fix things.  For people like me, and you I guess, that is Not Helpful.

To fix grub, it would be good to know your disk setup: which OSes are you running and on which partitions are they?  Which OSes do you expect to see in the bootloader?

---

### Post by drs305 on 2010-09-05
Edit: OP figured it out for himself. See post #4 for his solution.

Usually this type of message means that you have a bad entry in your fstab file.* Mount your real Ubuntu partition from a LiveCD, then open your real Ubuntu system's fstab for editing. You can run "sudo blkid" to check the UUID numbers and replace the faulty one, or change the entry (for now) to /dev/sdXY (XY being the correct partition designations).

```
sudo mount /dev/sdXY /mnt
gksu gedit /mnt/etc/fstab
```

Save the file, then reboot.

* However, you say you can boot to the PAE kernel? Is it on the same partition using the same fstab file? If it is, then you may need to change your grub menuentry: Edit the entry by highlighting it in the Grub menu during boot. Then highlight the problem entry and press "e". Remove the entire "search" line by holding down the DEL key on that line, and change the UUID line to read: 
 ... root=/dev/sdXY ...

---

### Post by calmblythe on 2010-09-06
PAE: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

It's all good now. I went into the non-PEA part, entered Synaptic Package Manager and just re-installed the "linux-image-2.6.32-24-generic-pae" package.

Thanks for your help, though.

---

