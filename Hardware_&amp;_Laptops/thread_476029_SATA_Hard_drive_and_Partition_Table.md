---
title: "SATA Hard drive and Partition Table"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by MadCowDzz on 2007-06-16
Hi all,

A simple question of whether or not this is normal:

I bought an SATA drive last year and never managed to install it successfully... it doesn't mount automatically, so I haven't really used it. Today, while poking around the innards of the case, I remembered I have the drive and figured I would approach installing it properly.

I ran **sudo fdisk -l** to check if it is listed... indeed the results indicate:
*Disk /dev/sda doesn't contain a valid partition table*

Just for the heck of it, I ran **mount /dev/sda /media/drive**
It mounted fine, and I discovered that I had placed files onto the drive last year... apparently, 60GB worth of data.

Ultimately, my question, is this normal. If there isn't a valid partition table, how am I able to add files?
Is it possible to fix this without losing the files?

What would be my next steps to ensure this drive gets mounted permenantly?

Thanks!

---

### Post by MadCowDzz on 2007-07-02
Perhaps I didn't explain it clear?
My ultimate question is: If a drive doesn't have a valid partition table, can it still be considered stable enough to use?
Do I have to erase the data to fix things? (Do I need to fix things?)

---

