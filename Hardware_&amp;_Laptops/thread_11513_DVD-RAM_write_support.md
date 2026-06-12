---
title: "DVD-RAM write support"
date: 2005-01-17
forum: Hardware &amp; Laptops
---

### Post by Ensis on 2005-01-17
Hi,

I'm trying to get full UDF and DVD-RAM support in a standard Ubuntu installation. 

I'm using a Toshiba SD-W2002 DVD-RAM drive. I can mount cdroms and automount works great, too. I even can read my DVD-RAMs, but I have no write support. Ubuntu tells me, the disc is not writeable. 

In the hardware manager below the SD-W2002 the value storage.dvdram is set to 1, but storage.cdrom.dvdram is set to 0.

Do I need udftools?

Thanks
Ensis

---

### Post by Ensis on 2005-01-21
I'm still searching for a solution.

I've installed and configured udftools and the udf filesystem module is loaded. But I'm still only able to read the discs. I've tested a dozen of new and used DVD-RAMs but I can't get write support.

Maybe there's nobody who can help, but does anybody of you uses UDF write support successfully with Ubuntu? Just to be sure, that it is possible with Warty.

---

### Post by Ensis on 2005-01-24
There is no one who uses DVD-RAM with Ubuntu?

---

### Post by jery_wang2002 on 2005-03-30
[QUOTE=Ensis]There is no one who uses DVD-RAM with Ubuntu?[/QUOTE]
 I use it too and I am in the same situation with you but different problems. I want to use my DVD+RW media as backup solution. So far, the solution I have is not reliable.

---

### Post by mindhaq on 2005-06-16
[QUOTE=Ensis]There is no one who uses DVD-RAM with Ubuntu?[/QUOTE]
I just found this thread looking for a way to use DVD-RAM just like big floppies, i.e. without the need for a burning program.

Actually, this is very easy :-)
Just change the line for the drive in /etc/fstab so that it is mounted in read/write mode:```
/dev/hdc        /media/cdrom1   udf,iso9660 rw,user,noauto  0       0
```That's all! Just insert a DVD-RAM medium, and it will be automounted, and writeable.

Update: Formatting a DVD-RAM with UDF (which is the preferred Filesystem for the DVD-RAM format) is also very easy.```
apt-get udftools
``` 
Among others you will get the the tool mkudffs, see the man page for all details. I was able to prepare a fresh DVD-RAM-disc with the following command:
```
mkudffs --utf8 --media-type=dvdram /dev/hdc
```
I still have to find out if data written on a disk prepared like that is readable in Windows as well.

---

### Post by dxps26 on 2007-08-09
ok, so, i tried the apt-get udftools command, but the terminal said it was an invalid command or something...
> is there a front end for UDFtools???
> can K3B be somehow integrated with UDF tools so that i can do my DVD-RAM disks in one app?
*P.S- currently using a Matshita DVD-RAM UJ-841S

---

### Post by Alchera on 2007-08-13
```
apt-get install udftools
```

---

