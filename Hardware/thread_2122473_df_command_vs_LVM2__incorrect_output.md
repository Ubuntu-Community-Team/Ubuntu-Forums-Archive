---
title: "df command vs LVM2 : incorrect output ?"
date: 2013-03-05
forum: Hardware
---

### Post by amedeo62 on 2013-03-05
HD 1 Tera with ubuntu only.
S.O. installed with alternate CD 10.04 LTS with LVM support upgraded to 12.04.
Output of 'df' command  / root  full  100%

```
 df
File system             1K-blocchi     Usati Disponib. Uso% Montato su
/dev/mapper/duetto-root  470566288 446415052    247800 100% /
udev                       1728464         4   1728460   1% /dev
tmpfs                       695628       980    694648   1% /run
none                          5120         0      5120   0% /run/lock
none                       1739068       156   1738912   1% /run/shm
/dev/sda1                   233191     61450    159300  28% /boot

```

added 100 GB by the command 'lvextend'     + 100GB

```
lvdisplay
  --- Logical volume ---
  LV Name                /dev/duetto/root
  VG Name                duetto
  LV UUID                ySC8Y0-3uWt-tNHe-FKlz-u9R5-64eC-YPXyZC
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                756,92 GiB
  Current LE             193772
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/duetto/swap_1
  VG Name                duetto
  LV UUID                rOAgkN-aehW-Y2ry-tCQw-R7ad-EPTG-bG9R5h
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                9,71 GiB
  Current LE             2486
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

```

lvsize  correctly switch  from   656,92 GiB to  756,92 GiB.

but 'df' output is  root  /  100% full.

also the command 
```
lvscan
  ACTIVE            '/dev/duetto/root' [756,92 GiB] inherit
  ACTIVE            '/dev/duetto/swap_1' [9,71 GiB] inherit
```

confim new dimension.

Unity say disk full !


 /root/.local/share/Trash/   is clean.
I clean the system with Tweak.





HD SATA.

Any ideas ? ?

Thanks in advance

---

### Post by Cheesemill on 2013-03-05
After resizing the underlying LV you then need to resize the ext4 filesystem on top of it to take up the free space...
```
sudo resize2fs /dev/mapper/duetto-root
```

For a good guide to LVM check out [this]("http://crunchbang.org/forums/viewtopic.php?id=19411") thread.

---

### Post by amedeo62 on 2013-03-09
Thank's a lot! 
Now all is OK !

---

