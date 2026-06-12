---
title: "After moving (copying) linux partition, some things are not right"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by Turin Turambar on 2006-01-19
Firstly, I realize my mistakes. When I moved from one drive to another, I didn't exclude the directories like "proc", "sys" or "media" and similar. But what are the exact consequences of doing this? Linux runs fine, except that I have some enormous disk space usage. Disks manager says that Linux uses almost 7.5gb, which I know is *not* right, since it used only 2 or 2.5gb before!
What can I do in order to fix that?

There's also another thing. Linux partition originally was on "hda6", but I moved it to another drive which has another partition installments, and now it's "hda5". However, if do a "update-grub", it still "updates" grub to hda6?! Or when Linux checks the drive after 30 or so mountings - it checks hda6 not hda5?! Why?

Thanks!

---

### Post by Turin Turambar on 2006-01-19
@bump@

I also checked the Device tab in System Monitor.

Here's what it says for device /dev/hda5: Total 4.7GB, Free 2.8GB, used 1.9GB.

Now, only the last part is valid (1.9GB of data is what I expected). But there's no 4.7GB, but 10GB of space in total!

Could someone please tell me what is going on here? Why do I get the different numbers in each program - Disks Manager says 10GB total, but only 2.5GB free (which means that 7.5GBs are used - yeah right!), while Sys. Monitor reports only 4.7GB of total disk space.

---

