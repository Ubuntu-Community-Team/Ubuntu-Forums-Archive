---
title: "Swap file not working?"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Paul T. on 2009-06-16
After doing a clean install of Ubuntu 9.04 onto my notebook, I booted from CD and used Gparted to resize partitions to max size, and resized swap file to 2Gb (2 x memory), all went well but now system monitor is telling me that 0 bytes of 0 bytes on swap file being used. Have I somehow disabled the swap file? If so how do I re-enable it?

Paul.

---

### Post by Amilo1718 on 2009-06-16
the OS doesn't need the use of the swap partition all the time...
especially when you have already a RAM of 1 gig
:popcorn:

---

### Post by Paul T. on 2009-06-16
I understand that system doesn't need swap file all the time, but prior to resizing partitions system monitor would report that swap file is using 0 bytes of 194 mb, now it's implying that swap file is 0 bytes?

---

### Post by Amilo1718 on 2009-06-16
what does gparted tell you about the size of your swap file?

---

### Post by boof1988 on 2009-06-16
> **Paul T. said:**
> After doing a clean install of Ubuntu 9.04 onto my notebook, I booted from CD and used Gparted to resize partitions to max size, and resized swap file to 2Gb (2 x memory), all went well but now system monitor is telling me that 0 bytes of 0 bytes on swap file being used. Have I somehow disabled the swap file? If so how do I re-enable it?

Paul.

The UUID for the swap partition is probably different (now that it has been resized).

Of many options, two of which are...
[LIST=1]
[*]Change the UUID (listed in your /etc/fstab) to match the UUID of the swap partition.
[*]Change the UUID of the partition to match the UUID listed in /etc/fstab
[/LIST]

I think that #1 is the easier of the two.

---

### Post by Paul T. on 2009-06-16
Thx all for the advice, ashamed to say problem was my fault..... during re-partitioning I turned swap file off in GParted and forgot to turn it back on, 'doh  :oops:

---

### Post by Paul T. on 2009-06-16
Seems I was a bit premature to say it's sorted. I can start swap file with GParted, but on rebooting it switches itself off again. :confused:

---

### Post by jimv on 2009-06-16
Easy to fix:

First use this command to get the UUID of your swap partition:

sudo blkid

Then put that ID in these two files:

/etc/fstab (where it says swap)
/etc/initramfs-tools/conf.d/resume (there's only one line in here)

---

### Post by Paul T. on 2009-06-17
> **jimv said:**
> Easy to fix:

First use this command to get the UUID of your swap partition:

sudo blkid

Then put that ID in these two files:

/etc/fstab (where it says swap)
/etc/initramfs-tools/conf.d/resume (there's only one line in here)

Jimv, followed your instructions and it worked, many thx. :D

---

