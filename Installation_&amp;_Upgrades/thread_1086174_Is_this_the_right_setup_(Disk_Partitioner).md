---
title: "Is this the right setup? (Disk Partitioner)"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by Rlad78 on 2009-03-03
[IMG]http://i217.photobucket.com/albums/cc292/ChipzMaster/Lin.jpg[/IMG]

SCSI1 is my hard drive and SCSI5 is a Flash Drive.

Is this the right format for installing Ubuntu 8.10 alongside Windows?

---

### Post by Pumalite on 2009-03-03
Looks O.K.

---

### Post by Rlad78 on 2009-03-03
Something really bad just happened (I think)

I had finally finished putting in the password for the encrypted file. The loader said scanning disk at 18%. I left the room for about 2 minutes and came back to find that my computer had shut off and Ubuntu was not one of my OS choices on startup.

Does this mean I have to start all over again!?

---

### Post by Rlad78 on 2009-03-03
K, so I think it worked, but I think I needed to make it primary instead of logical.

Is this right?:
[IMG]http://i217.photobucket.com/albums/cc292/ChipzMaster/Lin2.jpg[/IMG]

Please help. (I'm major noob at Ubuntu...)

---

### Post by oldos2er on 2009-03-03
Linux doesn't require any primary partitions, extended logical is fine.

---

### Post by Rlad78 on 2009-03-03
> **oldos2er said:**
> Linux doesn't require any primary partitions, extended logical is fine.

Then how do I use Ubuntu once I install it?
Is it supposed to appear on the OS list during startup?

---

### Post by oldos2er on 2009-03-03
When you install Ubuntu, it's bootloader (called grub) will be installed as well. You choose to boot Ubuntu from grub's menu, which you should see after POST.

---

### Post by Rlad78 on 2009-03-03
I think I just wiped windows off my computer o.o;
It keeps telling me to put a bootable device in my computer and it won't let me go to my OS menu.

I went back on to the cd and all the partitions are correct, but it won't let me get into windows or ubuntu.

What should I do?

---

### Post by oldos2er on 2009-03-04
Is your BIOS set to boot from hard disk?

---

