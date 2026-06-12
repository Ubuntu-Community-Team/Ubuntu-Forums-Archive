---
title: "[SOLVED] Booting disk in floppy drive"
date: 2008-08-17
forum: General Help
---

### Post by Rumpty on 2008-08-17
What entry do I put in Menu1st so that my floppy drive comes up on the booting options list?

I've tried:
title  Floppy
root   (fd0,0)
makeactive
chainloader +1

But I get an error message - error 11 - unrecognised device string.
Any suggestions please?

---

### Post by ichthus on 2008-08-17
I think it would be root(fd0).  The first number refers to the disk, the second to the partition, like (TypeDisk, Partition), and I'm not aware that floppy disks can be partitioned.  Most likely it's not, so you just have the (TypeDisk) in order to specify the disk as a whole.

---

### Post by Rumpty on 2008-08-17
We're getting closer. My menu1st is now

title		Floppy
root		(fd0)
makeactive
chainloader	+1

But it still doesn't work. There is a reaction from the drive, a momentary noise, but it still doesn't boot. The message is
error 12: Invalid device requested.
Any further thoughts?

---

### Post by caljohnsmith on 2008-08-17
Have you by chance first confirmed that your floppy disk is indeed bootable? (Can you set your BIOS to boot it and see, or tried it in another computer?)

Also, check to see if your /boot/grub/device.map has an entry like:
```
(fd0)	/dev/fd0
```

---

### Post by Rumpty on 2008-08-17
There wasn't an entry in device.map for fd0, so I put one in, but it didn't help. Still getting the error 12 message, as above. 

The disk in the drive is bootable, definitely. I have tried two disks.

---

### Post by Rumpty on 2008-08-21
Sorted it out eventually. What works is:

rootnoverify (fd0)
chainloader +1
boot

Having rootnoverify as one word was the important part.

---

