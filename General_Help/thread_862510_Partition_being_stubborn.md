---
title: "Partition being stubborn"
date: 2008-07-17
forum: General Help
---

### Post by codeking on 2008-07-17
I have a partition called Shared.  Just today, I have not been able to mount this partition.  First it says "you do not have permissions" then upon using nautilus in gksudo mode (or whatever the linux term is) it gives me an error of not being able to find something or another.

It works fine for Windows.

---

### Post by dracayr on 2008-07-17
> not being able to find something or another ? now that doesn't help, do you have more information? execute

sudo mkdir /mnt/win
sudo mount /dev/*partition* /mnt/win

and post the output. *partition* should be in the form sd* or hd* (not *shared*)

dracayr

---

### Post by codeking on 2008-07-17
both outputted nothing.

but now may i add upon restart Shared has disappeared entirely from Computer.  fdisk still says its there, though.

---

### Post by dracayr on 2008-07-17
well if it outputs nothing, it should work :) direct your file browser to /mnt/win after you executed those commands..

maybe I should clarify the partition names.. I did not mean literally "sd*", but sth. like sda2, hda1, etc.. It depends on your partitioning

dracayr

---

### Post by bodhi.zazen on 2008-07-17
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: 
[list=number]
[*]vfat (FAT) use dmask=027,fmask=137
[indent]more permissive permissions : dmask=000,fmask=111[/indent]
[*]ntfs use [ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/indent]
[/list]


_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)
[indent]Vista: Install the fs-driver using the "Windows XP compatibility mode"[/indent]

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

