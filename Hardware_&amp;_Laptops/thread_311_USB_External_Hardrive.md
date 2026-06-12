---
title: "USB External Hardrive"
date: 2004-10-12
forum: Hardware &amp; Laptops
---

### Post by jivens on 2004-10-12
I have an external Maxtor 40GB USB Hardrive (FAT 32). Under Disks in the Computer menu I see an icon for te drive, but cannot access it, any ideas? 
Thanks

---

### Post by nerotje on 2004-10-21
Hi,
I had same problems with a external box.
I have 2 of them, 
1) pre istalled en fixed WD120GB drive 
2) open case to put in one of my choise.

For 1 it was working out of box with suse 8.2
For 2 it didn't

The major diff is #1 has only 1 partition and the added #2 has 4 partitions.
The automount does not mount the logical drives in extended partition in my case, in MS terms spoken.
With a script I do it now by hand atm.

It looks to me only primary partition(s) will be automount by hotplug on the suse system.

Hope this helps.

---

### Post by Lemuel on 2004-10-21
I had the same problem, /dev/sda is going to be mounted. But if there are several partitions on /dev/sda that doesn't work. I changed it to /dev/sda1 in /etc/fstab , but that just allows me to get to that partition, but not to the rest of the harddrive. At least the icon now responds to a click in a senseful manner.

It seams that all mountpoint in /media/ are offered to be mounted in the graphical dialog. So with adding lines like```
/dev/sda6        /media/usb1     auto    rw,user,noauto  0       0
``` you can access these partitions easily, although I don't experience any automatical mounts.

---

