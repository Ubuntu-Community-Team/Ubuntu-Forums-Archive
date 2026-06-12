---
title: "mdadm problems"
date: 2009-06-17
forum: Hardware
---

### Post by DoneRightI.T. on 2009-06-17
Hello All,

I am attempting to create a software raid 5 array using mdadm. I have come as far as to install, create, format, mount, and sync the raid array.

The issue that I am having is that as soon as I restart, my system throws me into an ash prompt with (initramfs), providing me limited functionality, and thus far, the only resolve has been to boot from a livecd and remove mdadm, restart, and start again.

the Hardware:
/dev/sdb1 - 200GB
/dev/sdc1 - 200GB
/dev/sdd1 - 200GB

the raid has been created using the following:
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1

```
thus creating the raid array in **/dev/md0**

at this point I have modified the file **/etc/mdadm/mdadm.conf** to the following:
[I]DEVICE partitions
#ARRAY /dev/md0 level=raid5 num-devices=13 UUID=d9316af6:94745fa0:b3a4010d:90c0b7b2
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=4ebb7e93:99d91fe4:1457cee7:92a60921 spares=0
MAILADDR root[/I]

The reason for the first is unknown, as soon as I install and run 
```
mdadm  --examine  --scan --config=mdadm.conf
```

I get both of these listed. I don't have 13 disks, and am unaware where this is coming from. This problem or anomaly may not even be the source of the problem, however is quite confusing.

as well I note that both these devices show as having spares=1.. the output of the command is below:

[I]ARRAY /dev/md0 level=raid5 num-devices=13 UUID=d9316af6:94745fa0:b3a4010d:90c0b7b2
   spares=1
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=6c177099:91df6fa4:8f7cd46a:5917f08b
   spares=1[/I]

I would really like to have this up and running, and am curious to an even modest online resource; the man pages have not helped thus far and any advice would be greatly appreciated.


Sincerely,
Chris Thompson
Done Right I.T.

---

