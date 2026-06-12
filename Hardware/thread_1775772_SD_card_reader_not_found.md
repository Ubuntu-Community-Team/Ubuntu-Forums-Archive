---
title: "SD card reader not found"
date: 2011-06-05
forum: Hardware
---

### Post by RobertLos on 2011-06-05
Good morning,

After updating (in fact reinstalling) ubuntu 11.04 my 6-in-1 Card Reader is not working any more. Using lsusb the device lists properly:
```

Bus 005 Device 002: ID 07cc:0200 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader

```

When inserting (a working SD card or a CF-card) it does not appear as a drive in /media. There are however a few SD-drivers listed, but they are also there when no SD-card is inserted.

my fstab looks like this
```

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sdc1 during installation
UUID=136ce86f-0873-494f-a8b9-8fc1d6975778 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sdc5 during installation
UUID=0ce45a2a-4caa-4858-be81-5dbadca4b8b4 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=b2ffab85-f6b4-47e3-97a5-caca3f2a2f31 /var2		  ext3    errors=remount-ro 0        1

UUID=EA880B49880B142B 	/media/winxp-c  ntfs-3g quiet,defaults,rw 0 0
UUID=9A084F98084F7275   /media/winxp-d  ntfs-3g quiet,defaults,rw 0 0
UUID=EC3850AD38507892   /media/winxp-i	ntfs-3g quiet,defaults,rw 0 0

```

It used to work in previous ubuntu versions (though not very reliable).

Please advice

Thanks

---

