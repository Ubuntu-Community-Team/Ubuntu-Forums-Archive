---
title: "Can't Burn to Blank CD"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by pixelterra on 2006-12-17
Hi good people,

I'm pretty new to linux and am trying to "make the switch" as so many others.

I would appreciate some help understading why my ubuntu doesn't recognize blank CD's. My drive loads CD's with data on them just fine. I've attempted this process through various burning programs and from nautilis. I've also used CD from 2 different manufacure's  (I don't have more to try). Nothing I do gets a blank CD recognized.

Essentially the system doesn't recognize a blank CD as being present, and even when it "attempts to read" from it, the drive doesn't even move or make noise. WHen I insert the blank CD it sounds like the read process gets aborted early and then it goes silent. 

This is the output of the "cdrecord -prcap" command. This output is the same whether I am root or not, and whethere is a blank CD in, or a data CD
> 
**benlieb@toshiba-satellite:~$ cdrecord -prcap**
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schi lling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian. org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
cdrecord: No such file or directory. Cannot open '/dev/cdrw'. Cannot open SCSI d river.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .


I would really like to do something as simple as burn a CD, and this is pretty disappointing.

---

### Post by dolphinholmer on 2006-12-18
Try installing Gnomebaker from synaptic and see if you can get it working through this front-end

---

### Post by _Paladin on 2007-01-05
Hi Ubuntu community, 

It seems that I am having a similar problem.  I can not get one of my ubuntu machines to recognize blank cds, so that I can burn data to them.  What is stranger is that it will recognize rw's but not cd-r.  I know it works, because it was a windows machine before we "made the switch".  It will read cd -r with data written on it just fine also.
Thanks.

---

### Post by leep on 2007-01-05
My installation recognizes blnk cds and dvds, but it is unable to write on them, burning process both with gnome backer and serpentine aborts after few seconds.
It is possible it is something like a driver problem? Where can I verify this?
Thank in advance,
S.

---

### Post by alinuxfan on 2007-01-16
> **leep said:**
> My installation recognizes blnk cds and dvds, but it is unable to write on them, burning process both with gnome backer and serpentine aborts after few seconds.
It is possible it is something like a driver problem? Where can I verify this?
Thank in advance,
S.

I am having the same problem...gonna try searching the forums...

---

### Post by leep on 2007-01-16
I solved the problem investing 35 euros in a new dvd burner.

---

### Post by alinuxfan on 2007-01-21
I did the same...now just waiting on it to get here

snail mail...still cant email computer parts for some reason ](*,)

---

