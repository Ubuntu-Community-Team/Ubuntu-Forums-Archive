---
title: "Does i need dmraid when i use HP raid controller (raid1 mirror)"
date: 2012-04-21
forum: Hardware
---

### Post by senzacionale on 2012-04-21
I installed ubuntu server and then I activate HP raid controller (raid1 - copy)a dn now is raid activated. I am using SATA disks.

I also installed dmraid but i always get

```
mitja@ubuntu-server:~$ sudo dmraid -ay
RAID set "ddf1_MyRaid" was not activated
```

other data:

```
mitja@ubuntu-server:~$ sudo dmraid -b
/dev/dm-1:      4186112 total, "N/A"
/dev/dm-0:    483696640 total, "N/A"
/dev/sdb:    488397168 total, "9VYE2JX4"
/dev/sda:    488397168 total, "WCAT1E556562"
mitja@ubuntu-server:~$ sudo dmraid -r -f sil
no raid disks with format: "sil"
mitja@ubuntu-server:~$ sudo dmraid -r -f
dmraid: option requires an argument -- 'f'
mitja@ubuntu-server:~$ sudo dmraid -b
/dev/dm-1:      4186112 total, "N/A"
/dev/dm-0:    483696640 total, "N/A"
/dev/sdb:    488397168 total, "9VYE2JX4"
/dev/sda:    488397168 total, "WCAT1E556562"
mitja@ubuntu-server:~$ sudo dmraid -s
*** Group superset .ddf1_disks
--> Subset
name   : ddf1_MyRaid
size   : 488019072
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
mitja@ubuntu-server:~$ sudo dmraid -ay
RAID set "ddf1_MyRaid" was not activated
mitja@ubuntu-server:~$ sudo dmraid -r
/dev/sdb: ddf1, ".ddf1_disks", GROUP, ok, 488019106 sectors, data@ 0
/dev/sda: ddf1, ".ddf1_disks", GROUP, ok, 488019106 sectors, data@ 0
mitja@ubuntu-server:~$

```

how can i activate dmraid if i need it ofcourse. 

[HTML] dmraid - discover and activate software (ATA)RAID[/HTML]

---

