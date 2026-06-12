---
title: "Howto: Make sony ericsson usb transfers working"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by theh1982 on 2008-01-23
Having problems doing file transfers to your memory card ? 

This is what you should do * NOTE YOU WILL LOSE ALL YOUR FILES THAT ARE ALREADY ON THERE


check the device name :

**mount -l **

in my case /dev/sdc1

Unmount the device : 
**umount /dev/sdc1**

then: 

**sudo mkfs.vfat /dev/sdc1** (Format disk to vfat format)

*(mkdir /media/mydir)*

**mount /dev/sdc1 /media/mydir**

Happy copying :)

---

