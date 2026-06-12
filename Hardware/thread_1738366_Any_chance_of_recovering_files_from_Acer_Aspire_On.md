---
title: "Any chance of recovering files from Acer Aspire One?"
date: 2011-04-24
forum: Hardware
---

### Post by henryd1990 on 2011-04-24
Hi there

I have an Acer Aspire One ZG5 that just crashed and turned off the other day. When booted up, it displayed the following message "No bootable device"

I created a bootable usb drive with a newer version of Netbook Remix on it and have loaded that up so it's running live. My question is, is there anyway to recover files from the SSD hard drive and if so where would they be. I had a look and couldn't find anything so i'm wondering if there's any hope or if i should just go ahead with formatting and installing the new version on the hard drive.

I'd be grateful to hear anyone's thoughts on this matter

Thanks

---

### Post by pdwerryhouse on 2011-04-24
See if you can see the SSD drive under /dev

Your USB drive is probably /dev/sda, so your SSD drive will likely be /dev/sdb, so you might be able to mount the partitions like this:

mount /dev/sdb1 /mnt

or

mount /deb/sdb2 /mnt

(if there were more partitions, they might be /dev/sdb3, /dev/sdb4, etc)

If they are there, but it complains about errors when you try to mount them, then you might have to run a file system check on each of the filesystems:

fsck /dev/sdb1

---

### Post by henryd1990 on 2011-04-24
Where would i go to see if i can see the hard drive. I have no clue what im doing when it comes to this. It took a lot of reading to make that usb drive so if i sounded like i had some understanding of what i was doing in my original post, i can tell you that's not the case :)

---

### Post by henryd1990 on 2011-04-24
It looks like it can see my hard drive as it shows in the bios settings and it gave me the option to write to the SSD when i started the installation.

---

### Post by K_45 on 2011-04-24
Boot off the USB and select the "Try" option. *Do not *choose to write anything if you want to salvage your files. Then open up a Terminal and enter:

```
sudo fdisk -l
```

and post the output.

---

### Post by henryd1990 on 2011-04-24
I'm on a different computer so there may be some spelling mistakes. It says

fdisk [-b ssz] [-u] DISK        change partition table
fdisk -l [-b ssz] [-u] DISK     List partition table(s)
fdisk -s PARTITION              Give partition size(s) in blocks
fdisk -v                               Give fdisk version

Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give start and End in sector ( instead of cylinder) units
-b 2048: (for certain M0 disks) use 2048-byte sectors

---

### Post by henryd1990 on 2011-04-24
Is the SSZ the hard drive?

---

### Post by henryd1990 on 2011-04-25
Sorry to keep pestering but does this string of letters mean anything to anybody. It would appear that it can see the hard drive but what i'd like to figure out is if there's anyway to access it's contents (if any) from a live USB ?

---

### Post by K_45 on 2011-04-25
It might be. Boot the USB and in the live environment, enter in a terminal

```
gksu gparted
```

and post a screenshot of what gparted has to say about it.

---

### Post by henryd1990 on 2011-04-29
It bought up gparted and it said 

PARTITION "unallocated" 
FILE SYSTEM "unallocated" 
SIZE "7.52gb"
USED -
UNUSED -

---

### Post by henryd1990 on 2011-04-29
Terminal said "Invalid partition table on dev/sda -- wrong signature 0."

---

### Post by K_45 on 2011-04-29
If Ubuntu can't see the files, try another distro like slax

[http://www.slax.org/get_slax.php](http://www.slax.org/get_slax.php)

That live cd may do it, if not, I don't think you can recover the files.

---

### Post by henryd1990 on 2011-04-29
I may just go ahead and format it. Well i did just try but it doesn't seem to let me create a partition or erase and install the new version ubuntu on the drive

When im in gparted and click "Create Partition Table" it just comes up with the message "Error creating partition table"

A few error messages popped up during the installing stage too.

Is there a way i can format the drive and start from fresh?

---

