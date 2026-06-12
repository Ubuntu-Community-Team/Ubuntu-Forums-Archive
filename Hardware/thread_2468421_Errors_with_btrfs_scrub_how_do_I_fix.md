---
title: "Errors with btrfs scrub how do I fix?"
date: 2021-10-29
forum: Hardware
---

### Post by lance bermudez on 2021-10-29
I have Uncorrectable errors after doing a btrfs scrub I used to get no errors of any kind had power surge and the computer lost power. Turned it back on then did btrfs scrub and now getting "Uncorrectable errors" how do I fix this?

btrfs scrub output
$ sudo /bin/btrfs scrub start -Bd /home
```

scrub device /dev/sda3 (id 1) done
Scrub started:    Thu Oct 28 22:15:23 2021
Status:           finished
Duration:         1:26:08
Total to scrub:   471.02GiB
Rate:             78.55MiB/s
Error summary:    csum=1024
  Corrected:      0
  Uncorrectable:  1024
  Unverified:     0
ERROR: there are uncorrectable errors


```

some other btrfs command output
```


$ sudo btrfs fi show /home
Label: none  uuid: 29be8a72-c6c5-4401-9dcd-287d05ab1c55
	Total devices 1 FS bytes used 395.21GiB
	devid    1 size 930.56GiB used 471.02GiB path /dev/sda3

$ sudo btrfs filesystem usage /home
Overall:
    Device size:		 930.56GiB
    Device allocated:		 471.02GiB
    Device unallocated:		 459.54GiB
    Device missing:		     0.00B
    Used:			 396.46GiB
    Free (estimated):		 530.57GiB	(min: 300.80GiB)
    Data ratio:			      1.00
    Metadata ratio:		      2.00
    Global reserve:		 512.00MiB	(used: 0.00B)

Data,single: Size:465.01GiB, Used:393.97GiB (84.72%)
   /dev/sda3	 465.01GiB

Metadata,DUP: Size:3.00GiB, Used:1.24GiB (41.50%)
   /dev/sda3	   6.00GiB

System,DUP: Size:8.00MiB, Used:96.00KiB (1.17%)
   /dev/sda3	  16.00MiB

Unallocated:
   /dev/sda3	 459.54GiB

$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=29be8a72-c6c5-4401-9dcd-287d05ab1c55 /               btrfs   defaults,subvol=@ 0       1
# /boot was on /dev/sda2 during installation
UUID=a7c9b896-a543-45d0-a1db-2697c0e12560 /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=19A5-F11D  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda3 during installation
UUID=29be8a72-c6c5-4401-9dcd-287d05ab1c55 /home           btrfs   defaults,subvol=@home,compress=zstd,autodefrag 0       2


```

---

### Post by lance bermudez on 2021-11-01
was given this 
[https://superuser.com/questions/858237/finding-files-with-btrfs-uncorrectable-errors](https://superuser.com/questions/858237/finding-files-with-btrfs-uncorrectable-errors)

I get journal file /var/log... journal is truncated ignoring file

anyone have any idea on how to get by this

---

