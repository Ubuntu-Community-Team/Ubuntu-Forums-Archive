---
title: "USB devices won´t connect"
date: 2008-10-20
forum: Hardware
---

### Post by Nancy Dz on 2008-10-20
I don´t have the option to mount jump drives or digital cameras.  

Also in Preferences>Removable drives and Media there is no Storage tab so I can select ¨Mount removable devices when hot plugged" or "Mount removable media when inserted¨  on like my book for version 8.4 says was that in an older version only or am I missing something from my install?

I also tried to install disk management to do it and it didn´t recognize anything either.

Where do I enable my USB devices?

Thanks,

Nancy

---

### Post by tthtlc on 2008-10-20
how about just using a terminal and see the "dmesg" output?   the automatic hotplugging system should recognize the device somehow, and from the dmesg output u can easily mount it manually.

---

### Post by Nancy Dz on 2008-10-20
> **tthtlc said:**
> how about just using a terminal and see the "dmesg" output?   the automatic hotplugging system should recognize the device somehow, and from the dmesg output u can easily mount it manually.

Thank you for your help! :)

I think I fixed it by installing ¨Storage Device Manager¨.  It wasn´t installed, but if I have that problem again I will try that.  

My machine was also re-booting sometimes when I tried to plug a device in.  But it seems to be ok now.

I think the camera monitor program may have had my usb ports locked when it got stuck as well which may have been causing the re-boots but I am not sure.

---

