---
title: "HDD Recovery From An Accidental Format"
date: 2010-07-07
forum: Hardware
---

### Post by chippu on 2010-07-07
A few days back i downloaded lucid lynx (ISO) and was trying to write it to a Kingston pen drive when i opened the startup disk creator and clicked format, i accidentally formatted my Samsung 500GB backup drive (external).. all my backup data is in it. the minute i found out (which is just right after the format) i unplugged the usb cable in panic.. everything in it is now gone

please help me out from this tragedy.. these are 7 years of work backed up in this external HDD

any help is highly appreciated. thanks in advance

---

### Post by bcbc on 2010-07-07
Try testdisk... to install, make sure the universe repository is enabled (System, Administration, Software sources, on the first tab make sure universe is checked). Then either install using Synaptic, or from command line:
```
sudo apt-get install testdisk
```

To run it you'd use
```
sudo testdisk
```


The following quote is taken from [http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformatted_partition](http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformatted_partition)
> Recovery of reformatted partition

If the partition has been reformatted to another file system (FAT32 formatted as NTFS or vice-versa),
run TestDisk,
select the hard disk and the partition type
choose Advanced
select the partition
choose Type,
enter the value corresponding to the previous filesystem
choose Boot
choose RebuildBS
List
If you can see your files, choose Write and confirm
In Analyse, choose to rewrite the partition with the correct partition type.

Good luck

If that fails, then photorec (a tool that comes with testdisk) can recover files from the drive (regardless of format or new file system type), but you just get data files without name or directory info, so it's a little harder to identify all your files.

---

