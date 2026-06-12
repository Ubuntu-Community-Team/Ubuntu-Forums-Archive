---
title: "Mounting hardrive from lacie network space 2"
date: 2012-12-25
forum: Hardware
---

### Post by kamelie1706 on 2012-12-25
Hi,

I have a lacie network 2
[http://lacie.nas-central.org/wiki/Category:Network_Space_2](http://lacie.nas-central.org/wiki/Category:Network_Space_2)

It failed to reset so I have dismantle it and try to backup my data.

lsblk
```
sde       8:64   0 931.5G  0 disk 
&#9500;&#9472;sde1    8:65   0     1K  0 part 
&#9500;&#9472;sde2    8:66   0 929.6G  0 part 
&#9500;&#9472;sde5    8:69   0   251M  0 part 
&#9500;&#9472;sde6    8:70   0   7.8M  0 part 
&#9500;&#9472;sde7    8:71   0   7.8M  0 part 
&#9500;&#9472;sde8    8:72   0 831.5M  0 part 
&#9500;&#9472;sde9    8:73   0   855M  0 part 
&#9492;&#9472;sde10   8:74   0   7.8M  0 part 

```

The data is on sde2 partition. I assume this is xfs partition.

fdisk -l does not provide any information on sde hardrive.

"sudo mount -t xfs /dev/sde2 /media/test" returns
```
mount: /dev/sde2: can't read superblock
```

"sudo xfs_check /dev/sde2" returns
```
xfs_check: /dev/sde2 is invalid (cannot read first 512 bytes)
```

"sudo xfs_repair /dev/sde2" returns
```
Phase 1 - find and verify superblock...
superblock read failed, offset 0, size 524288, ag 0, rval -1
fatal error -- Input/output error

```

"sudo mdadm /dev/sde2" retuns
```
/dev/sde2: is not an md array
```

Any idea in which direction I should look?

THanks

---

### Post by kamelie1706 on 2012-12-26
Hi,
 
I will try testdisk later today
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
 
Any other tool you would see helpfull here?
 
BR

---

