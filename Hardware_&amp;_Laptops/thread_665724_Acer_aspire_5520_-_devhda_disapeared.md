---
title: "Acer aspire 5520 - dev/hda disapeared"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by mrga on 2008-01-12
Hi. With my lap everything was fine. But then i went to skiing. Today i start my lap and i can not watch movies or listen to music. I put a cd/dvd in my dvd-rom , cd starts to spin, but after few seconds nothing happens. I went to computer and there i click on cd rom 1 and get this mount: special device /dev/hda does not exist


less /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2443bc7-a272-440e-9a85-7c910bb89308 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=931c8c7c-e742-4136-addd-5c1dfc067670 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

ls -dl /dev/hda

no such directory

---

