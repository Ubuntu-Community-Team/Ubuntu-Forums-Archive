---
title: "HD Failure / Restore Help"
date: 2008-07-12
forum: General Help
---

### Post by strange_cathect on 2008-07-12
Hello,

I've determined that my HD is about to go out on me and I've go a full rsync backup of my /home partition.

I want to install a new HD, install Ubuntu on it, and then move my copy of the /home to the new hard drive.

Are there any good Howtos on this subject or any pointers?

Thanks

---

### Post by dracayr on 2008-07-12
a pointer: DON'T use cp to copy, tar up home, and then untar on the new partition, else file rights are not maintained

dracayr

---

### Post by strange_cathect on 2008-07-12
That is good advice; I have an rsych-ed copy of /home so I'm good.

I guess I just want some advice on how to proceed. I guess I'll start by putting in the fresh drive, booting up with the live CD and then installing Ubuntu.

But how to I proceed from there? How can I then substitute my copy of /home for the fresh one created during the install? Will I have permissions problems? I'm lost.

---

### Post by boblemur on 2008-07-12
you can simply boot into your live cd... make up all your partitions for home,filesystem, swap ...

put ur data back...

and then install ubuntu

and go manual and just point it at the 3 partitions ( remba to make sure format doesnt tick itself...)

---

### Post by strange_cathect on 2008-07-12
That sounds easy! I'm pretty sure that I can get to the point where I need to point the OS to /home. How would I inform the OS where /home is?

---

### Post by boblemur on 2008-07-12
in the installer, go and select manual configuration... and then you can click on each partition and then change filesystem type...(ext3 or rasierFS)

and then swap for swap

and then change mount point to / for your filesystem and /home for your home

tick format for the filesystem make sure its not ticked for /home....

and you cant format swap so dw about that... and what you should see will look prity much the same as your partition table now...

install gparted if you wana look at it...

---

### Post by coffeecat on 2008-07-12
> **dracayr said:**
> DON'T use cp to copy, tar up home, and then untar on the new partition, else file rights are not maintained

Not so! Check out man cp. :wink: cp -a would do nicely. I've used it myself. Permissions/ownerships/timestamps are preserved.

I agree, however, that tar is a much more elegant solution.

---

### Post by strange_cathect on 2008-07-12
So, once I've created all my partitions for the fresh installation, can I use Gparted to move the backup of /home from my backup drive to the new /home partition? Or do I use rsync? Or something else?

---

### Post by boblemur on 2008-07-12
you create the partitions and they will be blank....

you then copy your files back onto the new partition that will become home...

and once you have your home setup, in the Ubuntu installer you will be able to tell it that you want that to be your home and thats it simply change the mountpoint to be /home in manual config of the parition section of the install

---

