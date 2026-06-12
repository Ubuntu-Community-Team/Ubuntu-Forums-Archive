---
title: "Independent dual OS after Wubi install"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by imissthesun on 2009-08-06
I have installed Wubi in my Windows XP and decided to adopt Ubuntu as my main OS.

I'm not an expert at all regarding computers, so I hope you can advise me on which is the best way to follow in my situation and how to do it.  

The main reason I want switch to Linux is security. I'm coming from a virus and malware damage to my work and that was more than enough to decide it.  

I share this machine with other people that need Windows and they don't want a virtual machine inside Ubuntu. Besides, I thought it could be good to have two independent OSes in case one of them  have any problems to work. In this case I would have the other one still working.  

So, the idea I have in mind for this machine is have Linux as the main OS and keep my files protected from Windows, please!  I have two disk drives, one empty(for backups) and the other with XP and Wubi inside it, so I thought it could be a good idea (don't know really) to have Linux in the main disk and Windows in the other one(go away windows!), so to let XP break his house if he like that, and keep me safe from it. (You may know if this is something right to do or not).  

Another thing I am thinking about, is make an independent folder or partition outside the two OSes to make backups and share files between them. I like the Wubi idea to look inside Windows folders (I want it) and don't let Windows look inside Ubuntu, but if I want to make backups accessed from the two OSes I have to put them inside Windows, and I don't feel secure in there. Thus, if there's an independent folder/partition and one of the OSes don't work I will have those backups secure outside them, just like an external drive. Again... (You may know if this is something right to do or not).  

Something else: I found in this site [http://www.e-ghost.deusto.es/docs/articulo.virus.html](http://www.e-ghost.deusto.es/docs/articulo.virus.html) that a virus in Windows could gain access to a Linux partition with a software like “explore2fs” and modify anything within it. How this can be avoided?  

(Just to note, I need to keep files and data I have in Windows and would be good if I keep Ubuntu data too)  

Thank You in advance.

---

### Post by merlinus on 2009-08-06
You can certainly have xp on one hdd and linux on another, and grub will allow you to choose between them.  An ntfs partition will allow reading and writing by the two oses.

Without an additional driver, windows cannot see linux, but linux can see windows as long as its partition is mounted.

---

### Post by Partyboi2 on 2009-08-06
Hi, one option could be to migrate your current Ubuntu install to its own partition using [[COLOR=Blue]LVPM[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?").
Ubuntu can read/write to ntfs so it can access files on the windows partition if needed.

---

### Post by imissthesun on 2009-08-06
Thanks for your answers.

So, I have two options: Linux and Windows in different drives, or migrate my Ubuntu to a new partition with LVPM. Which is the better option (if there's any). Is there a real advantage about having them in different drives?

Thanks.

---

### Post by merlinus on 2009-08-06
You will need a linux partition whether you use one or two hdds.  The obvious advantage is that if one dies, the other will still work.

I would research LVPM, however, to ensure it does not lock you into some proprietary and therefore limiting format, as opposed to ext3, for example.

---

### Post by imissthesun on 2009-08-07
> **merlinus said:**
> I would research LVPM, however, to ensure it does not lock you into some proprietary and therefore limiting format, as opposed to ext3, for example.
Ohuuu, I have to study :confused:

Thanks

---

### Post by furuno on 2009-08-07
Hey, this is interesting, I've run Ubuntu as a wubi install until now, and I think I want to change it to real partition, I've read about LVCM and I guess I'll just ask a question here to make sure :

So, here's my current partition setup :
HDD 1 :
- Partition A : Windows 16 GB
- Partition B : Ubuntu 16 GB
- Partition C : Data 1 200 GB
HDD 2 :
- Single Partition : Data 2 232 GB
So, from what I know LVCM will move Ubuntu to another empty partition, is there's anyway to change my wubi install to independent install while using the same partition B?

Thanks in advance...

---

### Post by Partyboi2 on 2009-08-07
> **furuno said:**
> Hey, this is interesting, I've run Ubuntu as a wubi install until now, and I think I want to change it to real partition, I've read about LVCM and I guess I'll just ask a question here to make sure :

So, here's my current partition setup :
HDD 1 :
- Partition A : Windows 16 GB
- Partition B : Ubuntu 16 GB
- Partition C : Data 1 200 GB
HDD 2 :
- Single Partition : Data 2 232 GB
So, from what I know LVCM will move Ubuntu to another empty partition, is there's anyway to change my wubi install to independent install while using the same partition B?

Thanks in advance...
Can you open a terminal and post the output to
```
sudo fdisk -lu
```

---

### Post by furuno on 2009-08-07
Here it is :```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sector/track, 30401 cylinders, total 488397168 sector
Units = sektor from 1 * 512 = 512 bytes
Disk Identification: 0x14e214e1

Boot Devices        Start         End    Blocks     Id  System
/dev/sda1   *          63    34475489    17237713+   7  HPFS/NTFS
/dev/sda2        34475490   488375999   226950255    f  W95 Ext'd (LBA)
/dev/sda5        34475553    68950979    17237713+   7  HPFS/NTFS
/dev/sda6        68951043   488375999   209712478+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sector/track, 30401 cylinders, total 488397168 sector
Units = sector from 1 * 512 = 512 bytes
Disk Identification: 0xad5c9953

Boot Devices        Start         End    Blocks     Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS
```The output is localized so I'd try to revert it back to english...

sda1 should be my Windows partition
sda2 = wubi virtual disk ?
sda5 = Ubuntu partition (the partition I install ubuntu with wubi to)
sda6 = 1st data
sdb1 = 2nd data

---

