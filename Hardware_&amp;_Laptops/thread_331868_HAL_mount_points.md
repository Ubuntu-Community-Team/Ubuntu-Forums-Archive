---
title: "HAL mount points"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by null_pointer_exception on 2007-01-05
I have an ipod, thumdrive and external hard drive. I would like them to be mounted at /media/ipod, /media/thumb and /media/external respectively. Right now they are mounted as /media/sd?? which changes depending on which I plug in first. Is there any way to set up HAL to do this? (I have product_id, vendor_id and serial to work with.)

Thanks in advance for any response,

---

### Post by kidders on 2007-01-05
Hi there,

The place you need to look is /etc/udev/rules.d. You can use information like product serials/vendor info to have the kernel create /dev entries or symlinks for you. You can Google "udev rules howto" for help. Post back if you have any trouble!

---

### Post by null_pointer_exception on 2007-01-06
udev won't help because I don't care where the device files are, only the mount points. I have some basic HAL configuration now, but HAL seems to be ignoring my volume.policy.desired_mount_point values. Any ideas anyone?

---

