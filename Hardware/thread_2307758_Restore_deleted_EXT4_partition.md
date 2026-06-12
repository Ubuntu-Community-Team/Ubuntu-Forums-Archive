---
title: "Restore deleted EXT4 partition"
date: 2015-12-28
forum: Hardware
---

### Post by tomasz9 on 2015-12-28
Hi 
Yesterday I installed new ubuntu on my HDD.
I had 3 ext4 partitions one for new Ubuntu installation one for /boot and one for old Linux Mint.
During Ubuntu installation process I decided to remove old Linux Mint partition because earlier I copied data to my pendrive but my data on this pendrive is corrupted.
What I want to do is to recover my old Linux Mint partition. 
I have this "partition" as free space on disk I know the start block and end block.
I tried with testdisk but it didn't find lost partition and can't see this free space.
I tried to rescue partition with parted rescue start_sector end_sector and nothing happend

Is it possible to recreate partition with any other tool ?

Here is fdisk results

```
Device         Start       End   Sectors   Size Type
/dev/sda1       2048    616447    614400   300M EFI System
/dev/sda2     616448   2459647   1843200   900M Windows recovery environment
/dev/sda3    2459648   2721791    262144   128M Microsoft reserved
/dev/sda4    2721792 217083903 214362112 102,2G Microsoft basic data
/dev/sda5  217083904 218007551    923648   451M Windows recovery environment
/dev/sda6  853772288 855773183   2000896   977M Linux swap
/dev/sda7  851771392 853772287   2000896   977M Linux filesystem
/dev/sda8  218007552 851771391 633763840 302,2G Linux filesystem
/dev/sda10 934809600 976773119  41963520    20G Windows recovery environment
```

Missing partition is from sector 855773183 to 934809600


[B]Solved

I recover my partition using parted

I found that I didn't change units to sectors

before you start change units with command:

[/B]```
unit s
```

**after that run command:**
```
rescue start_sector end_sector 
```


Thank you for your help 
Best Regards
Tomasz

---

