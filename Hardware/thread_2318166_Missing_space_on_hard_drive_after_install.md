---
title: "Missing space on hard drive after install"
date: 2016-03-23
forum: Hardware
---

### Post by s0563764 on 2016-03-23
Hi,

recently wiped my hard drive to install ubuntu, but 20gb is missing from the drive. The hard drive should be 320gb, but is currently less than 300gb. I have tried wiping the drive again by installing lubuntu, but the problem is persisting. Had a look at the forums, I'm just booting through a live lubuntu CD to see there is anything else I can try.

The computer works fine apart from the hard drive issue. I'm not sure what information I need to provide, but gparted is only showing less than 300gb.

Thanks

---

### Post by weatherman2 on 2016-03-23
Please show the output of:

```

sudo parted -l

```

FYI, by default, the operating system reserves space on ext4 partitions - normally 5% I think.  You can change this value if you want, but it's not recommended for OS partitions (the one where / is mounted) unless you are really short on disk space.  See the tune2fs command:

[http://linux.die.net/man/8/tune2fs](http://linux.die.net/man/8/tune2fs)

---

### Post by SeijiSensei on 2016-03-23
The ext4 formatter sets aside a portion of the disk for root's exclusive use.  By default the fraction is 5%.  On modern large drives that's usually too much.  Try formatting the drive by booting from the installation disc, choosing Try Ubuntu, then opening a terminal.  Use the command
```
sudo mkfs -t ext4 -m 1 /dev/sda1
```
to format the first (or only) partition on the primary hard drive and reserve only one percent of the space.  Now reboot, run the installer, choose Something Else, and point the installer at the existing filesystem.  Tell it not to format the space before installation.

To see why this happens, read the description of the "-m" option on the [man page for mkfs.ext4]("http://linux.die.net/man/8/mkfs.ext4").

---

### Post by oldfred on 2016-03-23
My parted info says drive is 250GB, but gparted says 232GiB. Which is the same, but one is decimal and the other binary.

       [http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)
[http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)
It's the difference between gigabytes (GB) and gibibytes (GiB). One gigabyte = 1000 x 1000 x 1000 bytes (base 10). One gibibyte = 1024 x 1024 x 1024 bytes (base 2).

---

