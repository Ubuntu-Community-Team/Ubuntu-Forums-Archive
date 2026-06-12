---
title: "Drive crashed, made backup, superblock repair"
date: 2017-02-03
forum: Hardware
---

### Post by hardwaremonkey on 2017-02-03
My drive was crashing. The ubuntu 12.04 LTS would still start, but sectors on the drive were going bad. So I launched clonezilla and copied everything I could to a new drive. Then, I booted the 16.04.1 LTS live cd, and have attempted to mount my new hard drive without success. It seems "the superblock is bad." I am not familiar with what this means.

The following is what I have tried. I really need some direction as to try next to see if I can make this drive readable. I believe the partition is ext4, but I am not 100% certain.
```

[COLOR=#000000][FONT=Comic Sans MS]Error mounting /dev/dm-0 at /media/ubuntu/b0c6a16d-18d0-4ebc-8485-b9861b6c4747: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-0" "/media/ubuntu/b0c6a16d-18d0-4ebc-8485-b9861b6c4747"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/server2-root,[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]missing codepage or helper program, or other error[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]In some cases useful info is found in syslog - try[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]dmesg | tail or so.[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]Disklabel type: gpt[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]Disk identifier: 06968E25-4676-46D8-A5E2-BE04AA1ADC9B[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]Device  [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]Start    [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]End[/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]Sectors  Size Type[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]/dev/sda1[/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]2048 [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]391167 [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]389120  190M EFI System[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]/dev/sda2  391168 [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]890879 [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]499712  244M Microsoft basic data[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]/dev/sda3  890880 3907028991 3906138112  1.8T Linux LVM[/FONT][/COLOR]


[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo lvdisplay[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  --- Logical volume ---[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Path            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]/dev/server2/root[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Name            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]root[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  VG Name            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]server2[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV UUID            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]Oo6fwp-qUtw-1Y6E-RsGI-3IcK-RBCn-4P4U7F[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Write Access    [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]read/write[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Creation host, time ,[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Status          [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]available[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  # open             [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Size            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]1.81 TiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Current LE         [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]474802[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Segments           [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]1[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Allocation         [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]inherit[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Read ahead sectors [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]auto[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  - currently set to [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]256[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Block device       [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]252:0[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]  --- Logical volume ---[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Path            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]/dev/server2/swap_1[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Name            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]swap_1[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  VG Name            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]server2[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV UUID            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]bLXrTY-0Csb-5PGW-e5zz-xLjU-XC22-Xlbv9A[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Write Access    [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]read/write[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Creation host, time ,[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Status          [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]available[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  # open             [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV Size            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]7.89 GiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Current LE         [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]2021[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Segments           [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]1[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Allocation         [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]inherit[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Read ahead sectors [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]auto[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  - currently set to [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]256[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Block device       [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]252:1[/FONT][/COLOR]


[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo vgdisplay[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  --- Volume group ---[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  VG Name           [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]server2[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  System ID        [/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Format            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]lvm2[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Metadata Areas    [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]1[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Metadata Sequence No  3[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  VG Access         [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]read/write[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  VG Status         [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]resizable[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  MAX LV            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Cur LV            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]2[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Open LV           [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Max PV            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]0[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Cur PV            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]1[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Act PV            [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]1[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  VG Size           [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]1.82 TiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  PE Size           [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]4.00 MiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Total PE          [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]476823[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Alloc PE / Size   [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]476823 / 1.82 TiB[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Free  PE / Size   [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]0 / 0   [/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  VG UUID           [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]Y0nJsJ-mXiG-6NlF-pgRk-j7O2-n3TS-w9lWG4[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo modprobe dm-mod[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo vgchange -ay[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  2 logical volume(s) in volume group "server2" now active[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo lvscan[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  ACTIVE        [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]'/dev/server2/root' [1.81 TiB] inherit[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  ACTIVE        [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]'/dev/server2/swap_1' [7.89 GiB] inherit[/FONT][/COLOR]


[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo fsck.ext4 -n /dev/sda3[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]e2fsck 1.42.13 (17-May-2015)[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]Warning!  /dev/sda3 is in use.[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]ext2fs_open2: Bad magic number in super-block[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]fsck.ext4: Superblock invalid, trying backup blocks...[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]fsck.ext4: Bad magic number in super-block while trying to open /dev/sda3[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]The superblock could not be read or does not describe a valid ext2/ext3/ext4[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]filesystem.  If the device is valid and it really contains an ext2/ext3/ext4[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]filesystem (and not swap or ufs or something else), then the superblock[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]is corrupt, and you might try running e2fsck with an alternate superblock:[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]e2fsck -b 8193 <device>[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS] or[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]e2fsck -b 32768 <device>[/FONT][/COLOR]


ubuntu@ubuntu:/$ [COLOR=#000000][FONT=Comic Sans MS]sudo dmsetup mknodes[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ vgscan[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  WARNING: Running as a non-root user. Functionality may be unavailable.[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  /run/lvm/lvmetad.socket: connect failed: Permission denied[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  WARNING: Failed to connect to lvmetad. Falling back to internal scanning.[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  /run/lock/lvm/P_global:aux: open failed: Permission denied[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Unable to obtain global lock.[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo vgscan[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Reading all physical volumes.  This may take a while...[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  Found volume group "server2" using metadata type lvm2[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo vgchange -ay[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  2 logical volume(s) in volume group "server2" now active[/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:~$ sudo lvs[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  LV [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]VG  [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]Attr   [/FONT][/COLOR][COLOR=#000000][FONT=Comic Sans MS]LSize Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  root   server2 -wi-a----- 1.81t                                               [/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]  swap_1 server2 -wi-a----- 7.89g [/FONT][/COLOR]

[COLOR=#000000][FONT=Comic Sans MS]ubuntu@ubuntu:/$ sudo mount /dev/mapper/server2-root /data[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]mount: wrong fs type, bad option, bad superblock on /dev/mapper/server2-root,[/FONT][/COLOR]
[COLOR=#000000][FONT=Comic Sans MS]missing codepage or helper program, or other error[/FONT][/COLOR]

```

Thanks, in advance, for your help!!

---

