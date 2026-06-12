---
title: "How to write files bigger than 2GB on dvd with k3b"
date: 2005-11-06
forum: General Help
---

### Post by hellfire_bg on 2005-11-06
I have a dvd recorder Pioneer 107 and I use k3b o.12.2 to record dvds and cds. I`ve never before had to write dvds with single files bigger than 2GB so I hadn`t noticed the problem. Several days ago I had to make a data dvd with a single file, bigger than 2GB, the writing began, but finished less than a minute after it had started (it couldn`t have written the files for that short time since i used a 4x DVD RW it should have needed about 15 minutes) and when I mounted the dvd later there was nothing on it. I tried several times again with different dvds and i got the same result. Then i tried to make data dvds with several files each smaller than 2gb and I had no problems. This is the output k3b gave me:
> Waiting for media...
Growing ISO9660 filesystem on DVD+RW
Using growisofs 5.21 - Copiright ©..............
Found files bigger than 2gb. These files will be only accessible if mounted with UDF
Enabling UDF extension
Startred writing
Writing speed 5678 KB/s (4.10x)
Flushing the cashe may take some time
Modifying ISO9660 volume descriptor
Flushing the cashe may take some time
Writing the lead out may take some time
Average overall write speed 0.00 KB/s (0x)
Writing successfully finished

What should i do to write singles files, bigger than 2GB on a dvd with k3b or with another program (if k3b can`t do that).

Ubuntu 5.10
kernel - 2.6.12-9-k7

---

### Post by nSTKo on 2005-11-06
Well, maybe you can try NeroLINUX?

---

### Post by hellfire_bg on 2005-11-06
I tried Nero Linux. The result - it starts writing and writes for about 15 minutes (just as long as it should) and i get no error messages. When i mount the dvd the file is there but i it is only 383.9 MB big (i tried several times and it is always that big). I suppose i must change something in the preferences but i don`t know what exactly. Here are some options which i don`t know whether to check them or leave them unchecked.
Buffer-Underrun Protection
DVD High Compatibility Mode
UDF Options
UDF Partition Type - I can chose beteween 3 types - Physical partition; Virtual Partition; Sparring Partition
File System Revision - I can chose between - UDF 1.02; UDF 1.50; UDF 2.00; UDF 2.01
There are some other options but i don`t know whether they are important or know. How should i configure NERO Linux? And is there any way to burn dvds with single files bigger than 2GB

---

### Post by suRoot on 2005-11-06
One thing to check, in K3B in the "filesystem" tab of the "burn" dialog, make sure the "generate UDF structures" box is checked.

---

### Post by hellfire_bg on 2005-11-06
I checked it - the same result. Can you tell me has exatky is your k3b configured. I use the default settengs (i haven`t had problems with them before). The only change i made was to check "Generate UDF Stryctures" but it didn`t change anything.

---

### Post by suRoot on 2005-11-06
Sorry, but I'm not using K3B anymore.  I just remember that from past experience.

Maybe someone else can answer this, as I'm not sure, but how is UDF support in Breezy?  Does he need to install any packages to work with UDF volumes?  Is UDF support built in to the default kernel?

---

### Post by hellfire_bg on 2005-11-06
I`ve tried using gnomebaker as well but i have there the same problem and don`t know how to fix it. What do you use btw?
I don`t need to do it with k3b. I just need to get the job done so if you know any program in Linux that can do it (and if you now how to configure this program) it would be of great help to me.

---

### Post by magnusbb on 2005-11-06
I managed to burn a 2.3 GB ZIP file (a backup of my system) to a DVD yesterday. I inserted a blank DVD, and used the very simple **nautilus-burner.** It turned out to work perfect! Drag-and-drop the file, and click File -> Write to Disc.

---

### Post by hellfire_bg on 2005-11-06
Same result. I`m starting wonder if there is something wrong with my system... Any suggestions? I`m considering another possibility. I have another hard drive with NTFS file system and Windows XP installed. I will try to transfer the file to this hardrive and burn the files with the windows version of Nero but i know that by default linux cannot write onto a NTFS partition. There was however a solution to this problem. What should i do to be able to write on a NTFS partiton?

---

### Post by magnusbb on 2005-11-06
If you're using ReiserFS you can read this filesystem from Windows. Just google it, should be very simple. As of ext3 I don't know of any possibility reading this from Windows.

But writing to a NTFS partition from Linux should not be done. It is simply too dangerous, especially considering the size of your file. In the future I would recommend creating "an island" between your Windows and Linux system, ie. a FAT32 partition, which could be used for transfering and sharing files.

---

### Post by hellfire_bg on 2005-11-06
I have a FAT32 partition but you can`t have files bigger than 4GB on FAT32 and my file is 4.10 GB big. My linux FS i ext3 so i don`t have any ideas how could i see it under windows. Any ideas why i can`t burn files bigger than 2 GB?
BTW when i umount the dvd and then try to mount it again:
sudo mount -t udf /dev/hdd /media/cdrom0
I get:
 wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When try to mount it with:
sudo mount -t iso9660 /dev/hdd /media/cdrom0
I don`t have any problems.

---

### Post by NiN on 2005-11-06
[QUOTE=magnusbb]If you're using ReiserFS you can read this filesystem from Windows. Just google it, should be very simple. As of ext3 I don't know of any possibility reading this from Windows.

But writing to a NTFS partition from Linux should not be done. It is simply too dangerous, especially considering the size of your file. In the future I would recommend creating "an island" between your Windows and Linux system, ie. a FAT32 partition, which could be used for transfering and sharing files.[/QUOTE]

[http://www.fs-driver.org/](http://www.fs-driver.org/)

it's only a ext2 driver, but ext3 is compatible..

---

### Post by installer on 2005-11-06
[QUOTE=magnusbb]If you're using ReiserFS you can read this filesystem from Windows. Just google it, should be very simple. As of ext3 I don't know of any possibility reading this from Windows.

But writing to a NTFS partition from Linux should not be done. It is simply too dangerous, especially considering the size of your file. In the future I would recommend creating "an island" between your Windows and Linux system, ie. a FAT32 partition, which could be used for transfering and sharing files.[/QUOTE]

Explore2fs will read ext3 from XP just use it (from within windows) to transfer to ntfs.

[http://www.thetinternet.com/linux/rh_wt_view_linux.asp](http://www.thetinternet.com/linux/rh_wt_view_linux.asp)

---

### Post by hellfire_bg on 2005-11-07
> 
[http://www.fs-driver.org/](http://www.fs-driver.org/)

it's only a ext2 driver, but ext3 is compatible.. - I managed to write my file from windows. Thanks for the advise. What is left is to find out how to write files bigger than 2 GB from Linux...

---

### Post by NiN on 2005-11-07
Do you have the dvd+rw-tools package installed?

Maybe that could be the source of your problem..

---

### Post by hellfire_bg on 2005-11-08
I dvd+rw-tools installed. How can i use them?

---

### Post by tarasbulba on 2006-04-23
[QUOTE=hellfire_bg]I have a FAT32 partition but you can`t have files bigger than 4GB on FAT32 and my file is 4.10 GB big. My linux FS i ext3 so i don`t have any ideas how could i see it under windows. Any ideas why i can`t burn files bigger than 2 GB?
BTW when i umount the dvd and then try to mount it again:
sudo mount -t udf /dev/hdd /media/cdrom0
I get:
 wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When try to mount it with:
sudo mount -t iso9660 /dev/hdd /media/cdrom0
I don`t have any problems.[/QUOTE]


Hello,i have same problem too.I have burned 2 files each app. 2gb on a blank dvd in Windows.In windows i can access and work with those files.But in ubuntu,can't access or  open dvd.Says:
" wrong fs type, bad option, bad superblock on /dev/hdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"
I have search web.Nothing to do.any solutions?Thanks

---

### Post by tedrogers on 2007-02-03
I'm trying to write a 4GB system backup made with partimage to a DVD....this problem is annoying me too.

I used the simple Nautilus packet burner and I get a blank disc that burns way too quickly.

Using Gnomebaker also doesn't work.

I already have dvd+rw-tools installed.

I may try explore2fs, but I hate going back to XP just to do things like this. Why can't Ubuntu UDF burning properly?

Any ideas anyone?

---

