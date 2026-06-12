---
title: "Making sense of btrfs fi show output"
date: 2011-03-04
forum: Hardware
---

### Post by Koodoo on 2011-03-04
```
root@server:~# btrfs fi show
Label: none  uuid: <redacted>
	Total devices 1 FS bytes used 123.52MB
	devid    1 size 37.64GB used 3.04GB path /dev/sda7
```

I've checked with another tool, and the reported size was of 123.52MB. Why does it report 3.04GB? Is it normal?

EDIT: Also, the info given by btrfs' df still doesn't amount to 3.04GB:
```
root@server:~# mount /dev/sda7 /mnt
root@server1:/# btrfs fi df /mnt
Data: total=1.01GB, used=123.04MB
Metadata: total=1.01GB, used=492.00KB
System: total=12.00MB, used=4.00KB
```

---

