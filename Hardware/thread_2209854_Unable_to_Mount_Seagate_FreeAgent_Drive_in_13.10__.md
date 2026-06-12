---
title: "Unable to Mount Seagate FreeAgent Drive in 13.10 / Worked in 12.04 LTS"
date: 2014-03-07
forum: Hardware
---

### Post by Wbie on 2014-03-07
Pretty much a Linux newbie here although I have played around with Ubuntu for several releases. I recently upgraded to 13.10 with no regrets save for the inability to mount my external hard drive. Thing is, Ubuntu 12.04 LTS mounted the drive with no problem.


I've done quite a bit of googling and realize that Seagate drives don't always play nice with Linux. However, since 12.04 handled it flawlessly I'm hoping there will be an easy fix. The drive shows in Computer but a look at properties says every aspect (type, size, volume, etc) says "Unknown." When I click Mount I get a pop-up that says "Unable to mount location" up top and "Can't mount file" below.


Any help? Thanks in advance!

Note: I did a forum search and found lots on external hard drives, particularly Seagate drives, but nothing seemed to apply.

---

### Post by mikewhatever on 2014-03-08
You should probably post the outputs of the following two commands after plugging the device:
```

sudo fdisk -l

dmesg | tail

```
Most of external HDDs now have NTFS, and it wouldn't hurt to use Windows once in a while to check the file system.

---

### Post by Wbie on 2014-03-11
Figured it out.  Thanks for offering to help Mike.

---

### Post by BlinkinCat on 2014-03-11
> **Wbie said:**
> Figured it out.  Thanks for offering to help Mike.

Hi,

You should mark your thread as solved - [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Also you could add what you did to figure it out!

Cheers- :P

---

