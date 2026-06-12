---
title: "oops..might have made a partitioning mistake while installing??"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by agingric on 2009-03-20
hi,

i just installed ubuntu on my laptop.  everything working fine.  windows xp still works fine as well if i choose it as my OS.

i misunderstood what was happening during the partitioning process during the install and may have made a mistake.  i may have made one of the partitions too large, thereby decreasing the amount of space available to windows unnecessarily. then again, i could be be completely wrong.  

i booted up the machine with the ubuntu cd rom so that i could see how large each partition was.  here are my partitions.  my HD size is 80 GB

#1 primary  65.8 GB B ntfs
#5 logical  13.4 GB ext3
#6 logical  641.5 MB f swap swap
#2 primary  213.9 MB 

i think #5 may be larger than necessary??  is there a safe way to make it smaller so more space can be devoted to #1? 


thanks for any info you can provide.  i'm new to linux and don't know much yet :)

andy g

---

### Post by tommcd on 2009-03-20
> **agingric said:**
> hi,
  here are my partitions.  my HD size is 80 GB

#1 primary  65.8 GB B ntfs
#5 logical  13.4 GB ext3
#6 logical  641.5 MB f swap swap
#2 primary  213.9 MB 

i think #5 may be larger than necessary??  is there a safe way to make it smaller so more space can be devoted to #1? 


How much space do you need for Windows? The 65.8GB you show there should be fine as long as you have at least about 15% free space. Windows XP needs at least 15% free for the swap file and to completely defragment the drive.

As for Ubuntu, the 13.4GB is fine. This will give you enough room to to download data and files to your home partition  , as well as to install new programs.

Open a terminal (applications > accessories > terminal) andpost the output of:
```
sudo fdisk -l
```
and 
```
df -h
```
Unless you really need more space for Windows you should be fine though. Personally, I would use a lot more space for Ubuntu; and less for Windows, but it is your system.

And welcome to the Ubuntu forums! Welcome to the cool side of computing!

---

### Post by agingric on 2009-03-20
agingric@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13731372

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8000    64259968+   7  HPFS/NTFS
/dev/sda2            9704        9729      208845   88  Linux plaintext
/dev/sda3            8001        9703    13679347+   5  Extended
/dev/sda5            8001        9625    13052781   83  Linux
/dev/sda6            9626        9703      626503+  82  Linux swap / Solaris

Partition table entries are not in disk order

agingric@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              13G  2.7G  9.0G  23% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  120K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  372K  501M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-7-generic/volatile
/home/agingric/.Private
                       13G  2.7G  9.0G  23% /home/agingric/Private
/dev/sda1              62G   51G   11G  83% /media/SQ003520
tmpfs                 501M  2.0M  499M   1% /lib/modules/2.6.27-11-generic/volatile

---

### Post by agingric on 2009-03-20
is there a way to use itunes on ubuntu?  itunes is the main reason that i have so much room on my hard drive allocated to windows.  i get a lot of podcasts, which take up lots of space. .

---

### Post by tommcd on 2009-03-21
> **agingric said:**
> agingric@ubuntu:~$ sudo fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8000    64259968+   7  HPFS/NTFS
/dev/sda2            9704        9729      208845   88  Linux plaintext
/dev/sda3            8001        9703    13679347+   5  Extended
/dev/sda5            8001        9625    13052781   83  Linux
/dev/sda6            9626        9703      626503+  82  Linux swap / Solaris

Partition table entries are not in disk order

agingric@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              13G  2.7G  9.0G  23% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  120K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  372K  501M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-7-generic/volatile
/home/agingric/.Private
                       13G  2.7G  9.0G  23% /home/agingric/Private
/dev/sda1              62G   51G   11G  83% /media/SQ003520
tmpfs                 501M  2.0M  499M   1% /lib/modules/2.6.27-11-generic/volatile

Your partition sizes seem about right if you want to devote most of the space for Windows but still have enough room for using Ubuntu.

I'm not sure what the "/dev/sda3...Linux plaintext" is; and somehow your partitions are not in disk order as it says in the output of "sudo fdisk -l". This is not a problem though. So if you are not having any problems don't worry about it.

As for I-tunes, no, you can't install I-tunes on linux. You could if Apple would make a linux port for it; but don't hold your breath waiting for that to happen.
See this thread for alternatives to I-tunes in linux:
[http://ubuntuforums.org/showthread.php?t=1093040](http://ubuntuforums.org/showthread.php?t=1093040)
Sorry I took so long to get back to you on this.

---

### Post by agingric on 2009-03-22
i wound up moving the bulk of my podcast files off of my hard drive, onto my 60 gb ipod video which i have set up to use as an external hard drive in addition to normal ipod listening.  i also backed up all my music, pictures, documents, etc. onto the ipod.  at a later time, i'll back them up onto dvd rws.

then defragged the windows partition.  after that, i used a gparted live cd to partion my hard drive equally between windows and ubuntu.  everything working ok.  sweet!

---

