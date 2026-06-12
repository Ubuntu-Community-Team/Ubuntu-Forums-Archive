---
title: "mdadm &amp; USB"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by viking325i on 2007-05-25
Hi,

I have a 3 disk array (raid 5). Two drives are on internal IDE controllers and the third is on a USB external enclosure. When I reboot the array needs manual starting with -R (due to being incomplete) and requires me to re-add the external drive. Has anyone encountered a fix or work around for this?

Also I have recently got a USB2 to twin IDE adapter and have hung 4 IDE drives off this. It seems to work fine, with using "mknod /dev/md4 b 0 3" and then creating the array. However when I reboot and try to start or do anything with /dev/md4 I get "no such file or directory" am I creating my /dev/md point incorrectly or does mdadm not like USB devices?

Thanks

---

### Post by viking325i on 2007-05-25
Just thinking, is this due to mdadm comming up before USB drivers? if so how do I get USB to load up first?

Edit = I've got my 4 disk USB raid 5 comming up fine on boot, however the array with two internal IDE and one external on USB in raid 5 is always starting degraded. Any way I can get around that?

---

### Post by pyrosphere on 2007-06-17
I have the same problem. I have a 3 disk RAID5 array with usb drives that works fine when manually started but mdadm thinks it is degraded at boot because mdadm tries to assemble the array before all the usb drives are detected during boot up.

---

### Post by viking325i on 2007-06-18
I managed to get a fix for this after playing around. If you do a mdadm --detail /dev/md* (* being whatever device it is, probably md0 however).

Copy the UUID out, and then paste it into /etc/mdadm/mdadm.conf so it looks like 
ARRAY /dev/md4 level=raid5 num-devices=4 UUID=accf3b28:b992eb6a:b1ea8c7a:92ba9d$

Of course you will need to alter the UUID and /dev to match your one. Next reboot it will still be degraded, so rebuild it and it will be fine after that for all other reboots

---

