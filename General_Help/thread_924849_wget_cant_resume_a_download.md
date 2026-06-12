---
title: "wget: cant resume a download"
date: 2008-09-20
forum: General Help
---

### Post by thilinaVithanage on 2008-09-20
guys im downloading a debian iso and it stopped after a my computer switched off due to a power failure. When restarted the tried to resume download, but it stops saying the file is too large and cant resume.. 

------------command issued------------------
 $wget -c --progress=bar:dot [http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso)

--------------output-----------------------------------

thilina@debian:/mnt/wes$ wget -c --progress=bar:dot [http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso)
 
--2008-09-20 09:39:54--  [http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso](http://cdimage.debian.org/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso)
Resolving cdimage.debian.org... 130.239.18.173, 2001:6b0:e:2018::173
Connecting to cdimage.debian.org|130.239.18.173|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://laotzu.acc.umu.se/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso](http://laotzu.acc.umu.se/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso) [following]
--2008-09-20 09:39:56--  [http://laotzu.acc.umu.se/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso](http://laotzu.acc.umu.se/cdimage/weekly-builds/i386/iso-dvd/debian-testing-i386-DVD-1.iso)
Resolving laotzu.acc.umu.se... 130.239.18.158, 2001:6b0:e:2018::158
Connecting to laotzu.acc.umu.se|130.239.18.158|:80... connected.
HTTP request sent, awaiting response... 206 Partial Content
Length: 4693098496 (4.4G), 398131201 (380M) remaining [application/octet-stream]
Saving to: `debian-testing-i386-DVD-1.iso'

91% [+++++++++++++++++++++++++++++++++    ] 4,294,967,295 --.-K/s   in 0s      


Cannot write to `debian-testing-i386-DVD-1.iso' (File too large).

---------------------------------------------------------------------------

pls help me to resume the download.. Im having a 512kbps line and redownload will take another 30hrs..

---

### Post by Vivaldi Gloria on 2008-09-20
> **thilinaVithanage said:**
> my computer switched off due to a power failure. 

It's possible that the filesystem got corrupted. What kind of filesystem does it have? Have you tried fscking it?

---

### Post by mb_webguy on 2008-09-20
> **Vivaldi Gloria said:**
> Have you tried fscking it?

I have nothing to add to the thread.   I just have to do a double-take every time I see someone type that...  :biggrin:

I love Linux.

---

### Post by bingoUV on 2008-09-20
I see that the file you are trying to download is 4.4 GB in size. You are stuck at 91% which is uncannily close to 4GB, the file size limit of FAT32. wget insists that file is too large.

The Sherlock Holmes inside me says, the filesystem /mnt/west is a FAT32 filesystem. It can be easily verified. Just post here an output of the following command
```

mount

```

Solution: move the file to a partition of filesystem ext2/ext3. Or backup the files in /mnt/west, format it to ext3, and restore files.

---

### Post by thilinaVithanage on 2008-09-20
> **bingoUV said:**
> I see that the file you are trying to download is 4.4 GB in size. You are stuck at 91% which is uncannily close to 4GB, the file size limit of FAT32. wget insists that file is too large.

The Sherlock Holmes inside me says, the filesystem /mnt/west is a FAT32 filesystem. It can be easily verified. Just post here an output of the following command
```

mount

```

Solution: move the file to a partition of filesystem ext2/ext3. Or backup the files in /mnt/west, format it to ext3, and restore files.

yah the file system is fat32 ... 

ill just move the files to the ext3 and retry ...

---

