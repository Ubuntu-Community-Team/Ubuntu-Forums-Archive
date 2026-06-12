---
title: "Grub Intel Raid"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by SilentK on 2006-01-02
I have a dell xps with a intel raid controller. I currently I have two western digitals configured in a raid 0 array, ntfs file format with windows xp pro installed on it. I than have a maxtor drive with ubuntu installed on it. 
The raid 0 array takes up spaces hd1 and hd2 and the maxtor drive is in hd0 with grub installed on it.

What I would like to be able to do is at least dual boot (configure grub to boot up the raid 0 array) and if possible mount it. I've already installed dmraid but I am not really sure where to go from here.

---

### Post by kyri on 2006-01-02
What is the output from dmraid -r?

Do want to mount the ntfs partition? don't think there is support for that.  Or do you want to create an partition for ubuntu on the array?

-kyri

---

### Post by SilentK on 2006-01-03
the output of dmraid -r is
/dev/sdb: isw, "isw_bajbjcgehg", GROUP, ok, 156301486 sectors, data@ 0
/dev/sdc: isw, "isw_bajbjcgehg", GROUP, ok, 156249998 sectors, data@ 0

I don't really want to put ubuntu in the array as of now. Right now my main concern is to just get grub working so I don't have to go into my bios and disable the maxtor drive to boot into windows.

---

