---
title: "good bye windows"
date: 2005-11-26
forum: General Help
---

### Post by gheorghe_pop on 2005-11-26
What i want is to delete the windows partition.
My partitions is like this:
1.windows fat32
2.linux
3.data fat32

I want to resize the linux partition to take over the windows partition. I tried to make this with gparted but with no succes.
Please help.

---

### Post by Bachstelze on 2005-11-26
First you have to delete your windows partition. Then boot from a Live CD so your Linux partition is unmounted and you should be able to resize it.

---

### Post by gheorghe_pop on 2005-11-26
ok did that
now i'm using slaks and parted to resize partition:
#>parted
(parted) print
Disk geometry for /dev/hda: 0.000-19470.937 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
2       3812.300   8103.098  primary   ext3
3       8103.098   8597.285  primary   linux-swap
4       8597.285  19469.399  primary   fat32       lba

(parted) resize 2 0 8103.098
Error: Filesystem has incompatible feature enabled

what am i doing wrong?

---

### Post by Roman27 on 2005-11-26
This is definitely something I'm interested in doing as well.  I have the same setup.  Please post in here if you get it working gheorghe_pop.

---

### Post by Original Brownster on 2005-11-26
Hi,
I've done a fair bit of 'surgery' on disks in the past so I was curious about your problem. I checked the parted website and it says if your resizing an ext3 partition you cannot alter the start which is what your trying to do.

If your desperate to have a large partition then I'd backup your data and linux partition to dvd's or external media then delete hda1, hda2 and reformat as one ext3 partition. BUT you would need to modify grub and run the grub installation routine so that your system boots from hda1 which I doubt it does at present.
Something to be very careful with as if you make a mistake it'll leave your system unbootable. Recoverable with a live cd and some skill but not much fun if your new to it!

However an easier way to use the disk space is to reformat the windows partition as ext3 then use this to mount one of your linux partitions. you could for example mount all your /home directories on it or make a mount point for your music collection.
You would just copy the data into the new partition and edit your /etc/fstab file to mount the directory on the new partition. 
It's a safer option and less likely to cause you problems.

HTH

---

### Post by gheorghe_pop on 2005-11-26
hello
I was just tinking about the dvd backup. Can you sugest a howto for this.
You said i can't alter the start so,how about this:
I format the windows partition as ext3
Copy evrything from the second partition to the first one(old windows)
Delete the old linux partition
resize the current linux partition

---

### Post by Roman27 on 2005-11-26
[QUOTE=Original Brownster]Hi,
I've done a fair bit of 'surgery' on disks in the past so I was curious about your problem. I checked the parted website and it says if your resizing an ext3 partition you cannot alter the start which is what your trying to do.[/QUOTE]

I chose ReiserFS during install.  Can parted modify the start position with that filesystem?

---

### Post by Tiede on 2005-11-26
That would also work, puuuurrfectly so, in fact.
But as you will notice, it is very interesting/useful in linux to have your /home or other data directory on their own little mounting point. (if for nothing else than at least for accessibility/security)

---

### Post by Original Brownster on 2005-11-26
[QUOTE=gheorghe_pop]hello
I was just tinking about the dvd backup. Can you sugest a howto for this.[/QUOTE]

I dont know a howto as such though there might be one however assuming your going to need more than 4.2Gb I would use 'DAR' and there is also a graphical front end to it called KDAR.  Basically allows you to create slices that you can then burn to dvd.  There are a few directories that are typically not backed up and restored which you need to check, one being /proc which is dynamic and generated at boot time, 
I would have a quick look for people that have moved there distro around from one disk to another or similar.

> 
You said i can't alter the start so,how about this:
I format the windows partition as ext3
Copy evrything from the second partition to the first one(old windows)
Delete the old linux partition
resize the current linux partition

Yes there's no reason why you can't do this, subject to the partition being big enough :-) Whatever you do though be careful as you will need to understand how to get the grub boot loader installed correctly on your hard disk so that you can boot from the new partition. There are plenty of howto's and stuff and as long as your careful you should be fine. A live cd is always useful!

---

### Post by Original Brownster on 2005-11-26
[QUOTE=Roman27]I chose ReiserFS during install.  Can parted modify the start position with that filesystem?[/QUOTE]

Unfortunately no, check [here]("http://www.gnu.org/software/parted/parted.html") for more info.

---

### Post by kosmic on 2005-11-26
I think if you plan to expand your linux partition the best you can do is to read about LVM and do a fresh install using LVM, after that everytime you whant to expand the linux partition or put a new drive in your pc is easy as 2 or 3 comand lines :)

---

### Post by gheorghe_pop on 2005-11-27
I have a probblem with the backup of the linux partition.
I give this command:
```

tar cvpzf /mnt/mydata/backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/mnt/mydata/backup.tgz --exclude=/mnt --exclude=/sys

```

The problem is that the 'exclude' doesen't work and it's backing up even mnt and the other excludes.

---

### Post by kosmic on 2005-11-27
[quote=gheorghe_pop]I have a probblem with the backup of the linux partition.
I give this command:
```

tar cvpzf /mnt/mydata/backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/mnt/mydata/backup.tgz --exclude=/mnt --exclude=/sys

```
 
The problem is that the 'exclude' doesen't work and it's backing up even mnt and the other excludes.[/quote]
 
 
Why don't you try 'Partimage' is in the repos and is very easy to use :)

---

### Post by gheorghe_pop on 2005-11-27
Sorry.
Partimage is not the solution for me. It backups the entire partition which is verry big and i'm limited in space. I prefer tar but don't know how to exclude directories

---

### Post by Original Brownster on 2005-11-27
[QUOTE=gheorghe_pop]I have a probblem with the backup of the linux partition.
I give this command:
```

tar cvpzf /mnt/mydata/backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/mnt/mydata/backup.tgz --exclude=/mnt --exclude=/sys

```

The problem is that the 'exclude' doesen't work and it's backing up even mnt and the other excludes.[/QUOTE]

I think the --exclude option requires a pattern match so --exclude=/proc* might work, try it.

---

