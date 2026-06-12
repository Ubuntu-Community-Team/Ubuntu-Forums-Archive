---
title: "External Harddrive cant mount"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by Duffman on 2006-06-08
```
mount: wrong fs type, bad option,
 bad superblock on /dev/sda3, missing codepage 
or other error in some cases useful info is found in syslog -
 try dmesg | tail or so error: could not execute pmount


```

```

[4294688.670000] usb-storage: device scan complete
 [4294688.808000] Driver 'sd' needs updating - please use bus_type methods 
[4294688.810000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
[4294688.810000] sda: assuming drive cache: write through 
[4294688.811000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)
[4294688.811000] sda: assuming drive cache: write through 
[4294688.811000] sda: sda3 [4294688.827000] sd 0:0:0:0: Attached scsi disk sda 
[4294688.898000] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[4294688.996000] Buffer I/O error on device sda3, logical block 239607296 
[4294688.996000] Buffer I/O error on device sda3, logical block 239607297 
[4294688.996000] Buffer I/O error on device sda3, logical block 239607298 
[4294688.996000] Buffer I/O error on device sda3, logical block 239607299

```

This is what i get when i plug in my external hd, it worked on windows...
Duffman is online now   	Edit/Delete Message

---

### Post by xyz on 2006-06-08
Hi-
Would this help mounting it right:
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)
I've got an external HD,too and it works fine. Good luck!

---

### Post by Duffman on 2006-06-08
Thanks but it didnt work. :( Same error

---

### Post by Duffman on 2006-06-08
bump

---

