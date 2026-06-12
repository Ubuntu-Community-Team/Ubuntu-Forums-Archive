---
title: "dmraid + silicon image raid5"
date: 2011-07-22
forum: Hardware
---

### Post by eri75 on 2011-07-22
Hello guys,

this is my first post to Ubuntu forums. I am a newcomer who is recently running Live Ubuntu 11.04 on his WinXP PC after some serious crash happened.

I would like to access data in my Win partitions to back them up.

Now the issue:
I have a old ASUS mb with Silicon Image 3114 (fake)Raid controller configured in Raid5. On top of that I created two logical partitions which are seen as my Windows C: and F: drives.
I would like to mount them in Ubuntu but I could not succed so far. I have read a lot of posts about dmraid but noone seems to have the issue of multiple logical partitions inside the Raid5 array.

Output of dmraid -r is as follows:
```

eri@ubuntu:~$ sudo dmraid -r
ERROR: asr: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/dm-0" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/dm-0" to 4608
ERROR: hpt45x: seeking device "/dev/dm-0" to 18446744073709545984
ERROR: isw: seeking device "/dev/dm-0" to 18446744073709550592
ERROR: isw: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: isw: seeking device "/dev/dm-0" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: lsi: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/dm-0" to 18446744073709550592
ERROR: sil: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: via: seeking device "/dev/dm-0" to 18446744073709551104
/dev/sdc: sil, "sil_afagacacdjfe", raid5_ls, ok, 320171518 sectors, data@ 0
/dev/sdb: sil, "sil_afagacacdjfe", raid5_ls, ok, 320171518 sectors, data@ 0
/dev/sda: sil, "sil_afagacacdjfe", raid5_ls, ok, 312580270 sectors, data@ 0

```

So the three disks which makes up the array are seen and something is resulting from dmraid -ay:

```

root@ubuntu:/home/eri# dmraid -ay
ERROR: asr: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: ddf1: seeking device "/dev/dm-0" to 18446744073709420032
ERROR: hpt37x: seeking device "/dev/dm-0" to 4608
ERROR: hpt45x: seeking device "/dev/dm-0" to 18446744073709545984
ERROR: isw: seeking device "/dev/dm-0" to 18446744073709550592
ERROR: isw: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: isw: seeking device "/dev/dm-0" to 18446744073708468736
ERROR: jmicron: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: lsi: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: nvidia: seeking device "/dev/dm-0" to 18446744073709550592
ERROR: sil: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: via: seeking device "/dev/dm-0" to 18446744073709551104
ERROR: sil: wrong # of devices in RAID set "sil_afagacacdjfe" [3/0] on /dev/sda
ERROR: sil: wrong # of devices in RAID set "sil_afagacacdjfe" [3/0] on /dev/sdb
ERROR: sil: wrong # of devices in RAID set "sil_afagacacdjfe" [3/0] on /dev/sdc
RAID set "sil_afagacacdjfe" already active
ERROR: dos: reading /dev/mapper/sil_afagacacdjfe[Invalid argument]

```

Basically I get an error when I try to mount /dev/mapper/sil_afagacacdjfe. This is expected I guess, since that's not pointing to the actual logical partitions. Problem is that in /dev/mapper only sil_afagacacdjfe appears.

Can anybody suggest how to proceed?

Thx

---

### Post by eri75 on 2011-07-23
:(

---

### Post by eri75 on 2011-07-25
Up

---

### Post by eri75 on 2011-07-27
I found some more info about dmraid.

I could have two possible problems:

1. My kernel does not support RAID5, therefore the error message ERROR: sil: wrong # of devices in RAID set "sil_afagacacdjfe"

2. There might be some problems in the RAID set. As stated before, I had some files corrupted, but I am still able to boot Windows therefore partitions themselves are not corrupted.

How to verify I'm not stuck at 1? (I'm using Ubuntu 11.04 Live from a USB stick).

Thanks again in advance

---

### Post by Ubuntnoob32 on 2012-01-15
I have an identical setup, ASUS motherboard and I am using the Silicon Image onboard controller for a raid5 , single partition.  I wanted to use dmraid to read the raid 5 drive but I receive the same drive mapper error. 

Did you find a resolution?

---

### Post by eri75 on 2012-01-16
No I didn't
Just repaired windows installation and got access to my data.

Sorry for bad news

---

