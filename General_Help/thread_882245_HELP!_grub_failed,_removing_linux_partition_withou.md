---
title: "HELP! grub failed, removing linux partition without erasing windows."
date: 2008-08-06
forum: General Help
---

### Post by craigz on 2008-08-06
I have a dual boot on my laptop with windows xp and ubuntu. however, my grub failed and instead of being GUI its now a command prompt grub> when I start up my computer. I don't even know how to get Ubuntu to start and to get windows up and running I have to type, rootnoverify(hd0,0), makeactive, chainloader+1, boot. 

I needed linux for research I was doing but I no longer need it. I really needy the space though on my drive for windows. I had a partition of 7gbs set aside for linux on my D drive. I was wondering how to get rid of this without erasing everything on my computer. Can I just delete the partition in Partition Magic? Do I need to uninstall Ubuntu somehow? 

I only really know the basics of linux so be easy on me. Any help would be really appreciated. Thanks.

---

### Post by Locutus_of_Borg on 2008-08-06
you need to reinstall grub it looks


```
# grub-install --no-floppy /dev/sda
```

either from a livecd or from your grub prompt

run as root of course and substitute /sda for whatever your setup is

---

### Post by craigz on 2008-08-06
what is sda? i'm a n00b. eeek

---

### Post by caljohnsmith on 2008-08-06
If you're ready to get rid of Ubuntu, yes, you can just delete that partition, and give that space back to Windows if you like. But that will of course delete all of Grub's configuration files in /boot/grub, so you will no longer be able to boot. No problem though, because you won't need grub anymore on a Windows only machine. Just boot up your Windows installer CD, go to the recovery console, and use the command "fixmbr" and then "fixboot". That will replace Grub with the Windows XP MBR. You should be good to go after that.

If you don't have a Windows installer CD, another alternative is to use the [Super Grub Disk]("http://www.supergrubdisk.org/"), and it can reinstall the Windows MBR as well.

---

