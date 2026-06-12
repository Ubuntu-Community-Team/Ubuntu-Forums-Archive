---
title: "Installing a bigger disk on Lenovo R61"
date: 2009-05-09
forum: Hardware
---

### Post by jfl on 2009-05-09
The Lenovo laptop I got 18 months ago came with XP and a recovery partition.
I installed a dual boot Ubuntu (with a separate home partition) and happily upgraded Ubuntu to 8.04 and then 8.10.
It took me many hours to have everything running exactly the way I want.

Now, for some reason the 60Gb hard drive is becoming too small; had that happen to me before :rolleyes:
[B]
Question:[/B] How do I make an "exact copy" of the old drive to the new one, MBR and all.
Reinstall is out of question, too time consuming and I do not have the XP installation CD (was pre-installed).

The main office computer can connect to a 2.5" drive, but it is running W2K and I am not sure it has ~60Gb of free space.

What do you suggest ???

Thanks in advance :)

---

### Post by stefangr1 on 2009-05-09
What you absolutely need is something you can store your disk image on, like a server / network drive / usb drive.

Then you can use sysrcd to make an image of your current disk. After you placed the new drive, you can copy the image you made to your new disk. After that you can resize the partitions, or make new partitions in the unallocated space.

It is important to have a good backup in a procedure like this, but I guess you always have a backup; your old disk.

---

### Post by logos34 on 2009-05-09
> **stefangr1 said:**
> What you absolutely need is something you can store your disk image on, like a server / network drive / usb drive.

Not true. You can directly copy the hard disk with the **dd command**:

> [Cloning an entire hard disk:]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

[QUOTE]dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror

/dev/sda is the source. /dev/sdb is the target. Do not reverse the intended source and target. It happens. Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error.[/QUOTE]

Single command does it all.  Includes MBR.

---

### Post by jfl on 2009-05-09
> **logos34 said:**
> Not true. You can directly copy the hard disk with the **dd command**:



Single command does it all.  Includes MBR.

What you are saying is that I could copy (dd) the existing disk in my laptop to the new disk hooked up to the Windoze desktop via the network ???
How amI going to "share" a blank disk ???
If it could be done, it would be great !!!!!

---

### Post by logos34 on 2009-05-09
not networked

you'd need to connect the new drive directly to the lappy via usb enclosure (if you don't have one might as well get one so you can use the old 60 gb as a backup disk)

then boot from the ubuntu live cd, open a terminal and run dd

---

### Post by jfl on 2009-05-09
> **logos34 said:**
> not networked

you'd need to connect the new drive directly to the lappy via usb enclosure (if you don't have one might as well get one so you can use the old 60 gb as a backup disk)

then boot from the ubuntu live cd, open a terminal and run dd

Yeah, why didn't I think of it; sometimes I forget the simpler ways !!!
Thanks.

---

### Post by jfl on 2009-05-15
[FONT="Comic Sans MS"][SIZE="3"]**Thanks logos34 !!!**
Got the enclosure, booted from a live CD,ran the dd command - I had not realized how powerful that was - unmounted the partitions, gparted to the sizes I wanted.
Bingo, everything worked fine, I just need to find how to open the laptop and swap the hard drives.

Really appreciate the help !!![/FONT] [/SIZE]

---

### Post by logos34 on 2009-05-15
my pleasure.

enjoy ubuntu

---

