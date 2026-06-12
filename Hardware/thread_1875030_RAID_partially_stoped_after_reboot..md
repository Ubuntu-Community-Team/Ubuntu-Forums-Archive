---
title: "RAID partially stoped after reboot."
date: 2011-11-04
forum: Hardware
---

### Post by Azyx on 2011-11-04
After a reboot my RAID1 won't start. If I check mstat I get:

```
Azyx@DasDatorn:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sda1[0](S) <--[COLOR=Sienna] only partition inactive!![/COLOR]
      293036032 blocks
       
unused devices: <none>
Azyx@DasDatorn:~$
```If I check RAID Array in Disk-Utilities (palimpsest) it says:

State *[COLOR=Black]'Not running, partially assembled'[/COLOR]*, but under Action there are a button who says: [COLOR=Red]'Stop RAID Array'[/COLOR] and If I click that once It says:[COLOR=DarkGreen] 'Start RAID Array'[/COLOR],  And if I click again, it starts!

And mdsat gives:

```
Azyx@DasDatorn:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0] sdb1[1]  [COLOR=Sienna]*<--both partitions!!*[/COLOR]
      293036032 blocks [2/2] [UU]
      
unused devices: <none>
Azyx@DasDatorn:~$
```[B]It workes, but It's not away It should work, cos it only partially active after reboot!!
[/B]
First I added following to fstab:
```
UUID=f306072c-10fa-4f2e-9b72-b7f7f3afc380 /home/Azyx/300GB     ext4    defaults        0       1
```blkid gave me UUID for md0. But I inactivated that, cos I thougt that If fstab mounted it before it was ready, something maybe went wrong [COLOR=Red]BUT the error with partially working persist even without mounting in fstab.!![/COLOR]

/Cheers

---

