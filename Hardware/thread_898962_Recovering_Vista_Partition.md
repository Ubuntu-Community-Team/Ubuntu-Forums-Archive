---
title: "Recovering Vista Partition"
date: 2008-08-23
forum: Hardware
---

### Post by JeffoOfMetal on 2008-08-23
Here's the deal:

I've got a laptop that I dual-booted Vista and Ubuntu. Somehow, some of the files got deleted on the Vista partition and it is now unable to boot. I'm forced to use Ubuntu, which isn't a problem, but I can't recover that Vista partition, nor can I mount it through Ubuntu. When I try, this is the error message I get:

```
$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev'sda1': Operation not supported Mount is denied because NTFS is marked to  be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clickng on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown windows cleanly. Choice 2: If yo udon't have Windows, then you can use the 'force' option for your own responsibility. for example tyupe on the command line: mount -t ntfs-3g /dev/sda1 /media/Recovery -o force Or add the option to the relevant row in the /etc/fstab  file" /ddev/sda1 /media/Recovery ntfs-3g force 0 0
```

I obviously cannot perform the first option and the second option didn't work. I get this from the Terminal:

```
chris@chris-laptop:~$ sudo mount -t ntfs-3g /dev/sda1 /media/Recovery -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/Recovery: No such file or directory
chris@chris-laptop:~$ 

```

Please, what's a fix for this? 

pl0x

---

### Post by damis648 on 2008-08-23
Run in terminal:
```
sudo mkdir /media/Recovery
```
and then re-run:
```
sudo mount -t ntfs-3g /dev/sda1 /media/Recovery -o force
```
and it should work. To unmount it, run:
```
sudo umount /dev/sda1
```
Cheers!:popcorn:

---

