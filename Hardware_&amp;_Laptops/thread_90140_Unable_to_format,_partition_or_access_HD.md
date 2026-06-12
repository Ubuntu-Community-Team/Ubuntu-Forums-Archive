---
title: "Unable to format, partition or access HD"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by matt on 2005-11-14
I'm trying to see if a HD my friend has (which he messed up in an XP system) is salvageable. So first off, know that it may just be junk at this point regardless. In any case:

I installed the HD as a slave in my Breezy system. When I booted, I got a message, "primary slave drive fails." It allowed me to continue the boot, which I did. Once in Breezy, I tried dmesg, which gave me a massive number of I/O errors on hdb.

I tried GParted from a console, which can see the drive and how big it is, but not what partitions are on it. I tried to set a new disklabel unsuccessfully (error message). In the CLI, I get:

```
Error: Unable to open /dev/hdb - unrecognised disk label.
Error: Unable to open /dev/hdb - unrecognised disk label.
Error: Input/output error during read on /dev/hdb
Error: Input/output error during write on /dev/hdb
Error: Unable to open /dev/hdb - unrecognised disk label.

```

Trying fsck, I get:

```
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/hdb
Could this be a zero-length partition?

```

With fdisk:

```
Unable to read /dev/hdb

```

So, is there anything else I could try, or is this drive, as I suspect, NFG? Thanks for your help.

---

### Post by grendel_khan on 2005-11-14
If your machine will still access the drive, you might want to see if you can drag as much data off there as possible before it exploded into a heap of magnetic shrapnel. I'd use dd to try and image the drive, then work on that drive image, maybe using gpart if it can't even read the partition table.

You'll probably want to use the following technique (nicked from [this article](http://linuxweblog.com/node/236)). Note that you'll need a hard drive big enough, and with enough free space, to contain an image of the old one. As I was recently restoring a 2GB drive onto a 160GB drive, this was pretty simple for me, but your mileage may vary. If your broken drive is, as before, hdb:

```
$ sudo dd if=/dev/hdb conv=sync,noerror of=hdb.img
```

sudo because you need raw access to the device, conv=sync,noerror (no space after the comma!) to not die when the drive returns errors, as it undoubtedly will. If you want to see the progress, you can apt-get install **pv** and pipe it through as follows, but this is just for cosmetic purposes, and to assure yourself that the process hasn't stalled:

```
$ sudo dd if=/dev/hdb conv=sync,noerror | pv | sudo dd of=hdb.img
```

The article suggests piping the output of dd to gzip, to compress it. If you're low on space, that might be helpful, especially if the drive wasn't full.

If you can, capture information about the partition table and whatnot with the drive. If your system isn't detecting the partitions on the drives, you may be pretty well screwed on this part, but it'll save you some time when recovering the partitions later.

```
$ sudo fdisk -l /dev/hdb > hdb.info
```

So, now you have your drive image. Use the image! Remove the dying drive from your machine and don't fiddle with it more than absolutely necessary, as you might break something worse--better to mess arond with a copy instead.

Tools you might be interested in, which can operate on a disk image as well as on the actual device, include **parted**, **gpart** and **sfdisk**. Read the documentation and figure out what you want to do from there. Try not to image the actual physical drive more times than you have to, and don't write to it at all.

I just ran through this nonsense this past weekend. My sympathies, and best of luck to you.

---

### Post by matt on 2005-11-14
Thanks! I've got a day off coming up, so I'll give it a go then. Either way, thanks for the advice, and sorry to hear you had to go through the same thing!

Cheers.

---

