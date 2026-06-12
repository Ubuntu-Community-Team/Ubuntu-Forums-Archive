---
title: "flash drive format fail"
date: 2017-12-10
forum: Hardware
---

### Post by Kurt_Alan on 2017-12-10
Hello,

I had six bootable flash drives (msusb), all ubuntu DE's and obsolescent. In the process of bringinal all up to date I had no issues deleting partitions and formatting using the GUI Disks in Gnome 3. Success was confirmed after installing updated .iso's with mkusb and trying them out.

Two flash drives failed to reformat both with Disks and gparted, with various esoteric (to me) error messages. As a matter of efficiency, for the time spent troubleshooting these error messages, I could just as well throw them away and replace with Linux supported bulk Patriot flash drives that cost $5.00 each. So I think I'll forego troubleshooting these error messages, and that's why I do not include them.

But using terminal, is there a sure-fire way I can force a re-format? If so, what would be the steps and syntax?

Thank you!

---

### Post by ajgreeny on 2017-12-10
If the flash drives are not dead, which can happen sometimes, you may find that using mkusb again, going to the wipe menu and from there to the top item, **Standard: create MSDOS partition table with FAT32 partition**, does the trick for you.

You could also try gparted to create a new PT on the flash drive as above.

---

### Post by oldfred on 2017-12-10
+1 on ajgreeny's suggestion.

The issue is the hybrid ISO.
That is an ISO configured for both DVD or flash drives, but then dd is used (perhaps under the hood) to copy ISO to flash drive. But then flash drive does not have standard partition table and may have random data in partition table location on drive which then partition tools cannot correctly see.

Details:
[https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device](https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device)

---

### Post by Kurt_Alan on 2017-12-10
Thank you for the explanation. Did not realize mkusb had a wipe menu. That worked like a charm.

---

### Post by ajgreeny on 2017-12-11
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

