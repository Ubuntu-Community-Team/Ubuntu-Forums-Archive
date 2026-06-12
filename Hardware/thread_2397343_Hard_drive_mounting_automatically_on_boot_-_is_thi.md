---
title: "Hard drive mounting automatically on boot - is this a sign the drive is dying?"
date: 2018-07-28
forum: Hardware
---

### Post by sidneyshaw on 2018-07-28
As title, one of my drives is mounting automatically when I log in, though I've never configured it to do so.

Could this possibly mean the drive is on the way out?

---

### Post by coffeecat on 2018-07-28
More likely that things are working exactly as expected, but you need to provide more details for a definitive answer. Version and flavour of Ubuntu? External hard drive, or partition on an internal drive? Filesystem type? What is the mountpoint it gets mounted to?

For example, if you have an external USB drive formatted with a compatible filesystem plugged in and powered up when you boot up with Ubuntu, it will get mounted to /media/*YourUsername*/*name_derived_from_partition_label_or_UUID*.

---

### Post by sidneyshaw on 2018-07-28
Sorry, I should have said.

It's Xubuntu 18.04. Internal harddrive, formatted to ntfs. Mounts to /dev/sdb

I wouldn't have given it a second thought if not for several drive deaths in the last few months, but this one is only 9 months old. WD blue.

---

### Post by Skaperen on 2018-07-29
failure in the drive would cause the opposite problem and it would *not* mount.  so it used to not mount (now it does) and you didn't worry about it then?

---

### Post by sidneyshaw on 2018-07-29
> **Skaperen said:**
> failure in the drive would cause the opposite problem and it would *not* mount.  so it used to not mount (now it does) and you didn't worry about it then?


No, It's always mounted fine, but only when I've told it to do so. None of my other drives do this, but this one does, making me wonder if something could be wrong with the cable or connector. I don't know much about what could cause this, but surely non-system drives (well, only 1) shouldn't be mounting on log-in unless I've configured it to do so? I want to know why that's happening and why it's only happening to that drive, because it's a fresh install.

---

### Post by deadflowr on 2018-07-29
As already stated the fact that it is mounting usually means the opposite of failure.
But if you really have an itch to know for sure run SMART tests against the drive:
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

Also, how fresh an install?
Has this been happening since the new install?
Or did this behavior start out of no where well after the install (like weeks after)

Have you look at the saved session settings?
Perhaps that's doing something.

---

### Post by coffeecat on 2018-07-29
> **sidneyshaw said:**
> Internal harddrive, formatted to ntfs. Mounts to /dev/sdb


/dev/sdb is a device not a mountpoint, and you would be mounting a partition, not a whole device. That being said, I would not expect an internal partition to be automounted. Normally there would need to be an entry in /etc/fstab for it.

[quote=sidneyshaw]unless I've configured it to do so? [/quote]

Perhaps when using the Disks utility you did so inadvertently? Let's see some terminal output. Post the output of these two commands:

```
cat /etc/fstab
sudo blkid
```

Please post the output between [noparse]```
 and 
```[/noparse] BBCode tags for clarity and to retain formatting. There's a link in my sig if you're not sure how to do that.

---

