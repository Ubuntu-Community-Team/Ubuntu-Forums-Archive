---
title: "IBM Thinkpad T42p + ubuntu 6.06"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by simone.brunozzi on 2006-06-28
Hi there,
I have a simple basic question regarding the installation of Ubuntu on IBM Thinkpad T42p with intel centrino, dual booting with the original win XP.

When I examine the disk, there are two partitions: one 55 GB NTFS, and one 4.4 fat32, that is NOT usable under windows, and that contains files related to IBM recovery procedure and similar.

I want to repartition the NTFS partition to free space for ubuntu and swap, but I'm not sure that this will work, and will not cause pain to IBM preinstalled software.

I was wondering if some of you successfully installed a dual boot on such a machine.

Thanks!

---

### Post by slimdog360 on 2006-06-28
Im running a ibm R50e and ubuntu works fine, all the buttons and everything.
Im pretty sure gparted on the ubuntu install disk can do what you want, Im almost certain.

---

### Post by punda on 2006-06-28
[QUOTE=simone.brunozzi]

I was wondering if some of you successfully installed a dual boot on such a machine.

Thanks![/QUOTE]

Hem... If you "cut"  the NTFS partition, You'll have to reinstall the ThinkPad from recovery disks, and once you "cut" NTFS partition, the recovery partition becomes "magically" unusable....

look at 
[http://www.thinkwiki.org/wiki/Rescue_and_Recovery](http://www.thinkwiki.org/wiki/Rescue_and_Recovery) and the entire wiki for more informations...
or write me (anche in italiano ;-)
 
ciao,

--
Punda

---

### Post by compmodder26 on 2006-06-28
I have it installed on T60 dual booting with XP and the ThinkVantage Partition.  I successfully resized the NTFS partition using gparted on the Ubuntu CD.  The only thing that doesn't work is the ThinkVantage button.  However, GRUB will still give you the option of booting the ThinkVantage partition.

I will admit that with the beta 1 of Ubuntu, gparted wiped my entire hardisk.  But the final release worked fine.  So to be safe, make sure you make some recovery CDs.

---

### Post by gawron on 2006-06-28
I just did a dual boot installation on my T42. Made a quick & dirty howto - have a look here - [http://gawrysiak.org/corvus/?p=4](http://gawrysiak.org/corvus/?p=4)

---

### Post by simone.brunozzi on 2006-06-29
thanks everybody, I'll give it a try, after looking at the suggested web sites.

Cheers,

---

### Post by simone.brunozzi on 2006-06-30
Hi there again.

I successfully partitioned the hard drive and installed ubuntu on /dev/hda3 and created a swap partition. I created the ubuntu.img file, and put it into C:\

I'm almost done, but I can't solve this:
in my C:\ I don't have any boot.ini file, as suggested in the howto.

other files are: autoexec.bat, bootlog.prv, bootlog.txt, ccrrec.ver, config.sys, drivez.log, io.sys, logfile.txt, syslevel.ibm, tcpachip.log

Now I'm stuck... how can I tell windows to boot ubuntu too?

Cheers,

(edited): I solved the problem... it was well hidden!

---

