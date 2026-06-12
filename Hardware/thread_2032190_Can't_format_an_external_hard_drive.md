---
title: "Can't format an external hard drive"
date: 2012-07-23
forum: Hardware
---

### Post by donmatas on 2012-07-23
Hi,

I have a HDD of 500Gb. I am trying to give format to it (Ext4) with gparted and directly by clicking the right boton over the device icon and choosing "format". I have got the following error message:

```

Error formatting volume
Error creating file system: helper exited with exit code 1: 2002: error writing 131072 bytes: Success

```

Thanks,

Dm

---

### Post by TheFu on 2012-07-23
[http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/](http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/) should help.

Did you create a partition to hold the file system first?

---

### Post by donmatas on 2012-07-23
> **TheFu said:**
> [http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/](http://www.howtogeek.com/howto/17001/how-to-format-a-usb-drive-in-ubuntu-using-gparted/) should help.

Did you create a partition to hold the file system first?

Thanks TheFU for your help. I did exactly what the tutorial of the link says but I got an error. I remark that the tutorial does not say anything about make any partition in order to hold de file system. What do you suggest exactly?

Actualization: I tried the format de device with disk-utility and it works but now I can't mount the hdd. It gives me the following error:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Best,
DM

---

### Post by donmatas on 2012-07-23
I solved by creating an extended partition with gparted. After that I create two logical partitions (ext4 and ntfs)

thanks
M

---

