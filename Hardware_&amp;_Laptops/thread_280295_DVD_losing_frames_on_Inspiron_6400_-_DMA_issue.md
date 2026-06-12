---
title: "DVD losing frames on Inspiron 6400 - DMA issue?"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by mcglnx on 2006-10-19
Dear All,

I just received a new Insprion 6400 but got issues with the DVD player loosing frames.

I cannot use hdparm to set up the DMA because the CD is binded with /dev/scd0. 

I tried to:
- change the boot parmaeters as described in [http://domrep-jamaica.blogspot.com/2006/05/new-laptop-dell-inspiron-6400.html](http://domrep-jamaica.blogspot.com/2006/05/new-laptop-dell-inspiron-6400.html)
- force mounting with /dev/hdc
- used sdparm --set=WCE /dev/scd0 but got the error:
[INDENT]   /dev/scd0: TSSTcorp  DVD+-RW TS-L632D  DE03  [pdt=0x5]
>> warning: peripheral device type (pdt) is 0x5 but acronym WCE
   is associated with pdt 0x0.
WCE         1  [cha: y, def:  1]
[/INDENT]

[http://www.ubuntuforums.org/showthread.php?t=30949&page=1&pp=10&highlight=enable+DMA](http://www.ubuntuforums.org/showthread.php?t=30949&page=1&pp=10&highlight=enable+DMA)

None of those strategies were sucessfull,

I'm quite lost here - does any body was able to configure the DVD correctly?

Thanks,
M

Followed the page in

---

### Post by mcglnx on 2006-10-24
Solution found. See: [http://ubuntuforums.org/showthread.php?p=1657990#post1657990](http://ubuntuforums.org/showthread.php?p=1657990#post1657990)

---

