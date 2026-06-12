---
title: "Clone a hard drive From Linux"
date: 2010-07-10
forum: Hardware
---

### Post by transporter_ii on 2010-07-10
I have a dual boot ubuntu/XP machine with no CD-ROM, but it does have an eSATA port w/ an eSATA docking station.

I want to boot in Linux and copy the XP installation to a drive in the eSATA dock and have that copy be basically a bootable clone of my normal XP install.

I've never done this from Linux so I'm looking for some input from more knowledgeable users on the easiest way to do it.

I've always used a program and a bootable CD, but I can't do that in this setup because there is no CD-ROM.

Thanks,

---

### Post by mikewhatever on 2010-07-10
You can clone the partition with Partimage, making it boot is a different story, however.

---

### Post by IcarusR on 2010-07-11
There are several clone (as well as other) tools on 'hirens boot cd' which is available to d/l. Google for it.

---

### Post by transporter_ii on 2010-07-11
OK not sure what good a boot CD would do when I pointed out the machine has no CD-ROM. Partimage looks OK but its website says it copies a partition and saves it as an image. That doesn't seem to be the right tool, either.

For the record, I was able to boot to Ubuntu and install grsync, which is basically a graphical rsync. I just copied from the XP / NTFS partition in the machine to the (already NTFS formatted) HD setting in the eSATA dock. 

I was able to boot from the cloned drive sitting in the eSATA dock after this. I did get a couple of strange errors, but it seems to work OK for what I needed to do.

It was also way slower than imaging a HD. Doing an image usually takes me 20 - 30 minutes. Usuing grsync took me almost an hour to copy everything between the drives.

But thanks for the input. Partimage may be useful in the future.

Thanks,

---

### Post by IcarusR on 2010-07-12
> OK not sure what good a boot CD would do when I pointed out the machine has no CD-ROM.

Apologies not reading properly !

You could always put the image onto a usb drive & boot from that.
Hirens is very good to have handy, has saved me a couple of times.

---

### Post by C.S.Cameron on 2010-07-12
```
dd if=/dev/sda of=/dev/sdb
```
when run from the Live CD will make an exact bootable clone of sda on sdb, partitions and all.
sdb must be larger than sda.

---

### Post by licotto on 2010-08-01
When I type in the Terminal command above, I receive this message:
dd: opening `/dev/sda': Permission denied

What am I to do to overcome this? I thought it maybe needed the sudo command, but that doesn't seem to do anything.

Any help?

---

