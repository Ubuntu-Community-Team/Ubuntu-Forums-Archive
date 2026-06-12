---
title: "How to setup Raid 1 array for storage in Windows and Ubuntu?"
date: 2017-02-12
forum: Hardware
---

### Post by G4MAC on 2017-02-12
I recently purchased two 3 TB HDD to use for storage in a raid 1 configuration. This storage will not be a boot device at all. I have an SSD dedicated to Windows 10 and an SSD dedicated to Ubuntu. I would like both of these operating systems to be able to connect to the raid array and utilize it. 

I have read that this is possible through a FakeRaid but cannot seem to get Ubuntu to see it. Ubuntu only sees the individual drives. 

```
$ ls /dev/mapper/
control
```

```
$ sudo dmraid -r
no raid disks
```

```
$ sudo dmraid -ay
no raid disks
```

I would appreciate anyone's help to solve this problem.

Thank you

---

