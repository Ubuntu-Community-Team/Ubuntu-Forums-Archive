---
title: "terabyte drive only showing 860 GB"
date: 2009-04-23
forum: Hardware
---

### Post by djtecha on 2009-04-23
Hello all,
  So I just installed a terabyte drive and installed 9.04 to another drive, in the process of this the terabyte drive got mounted in the / folder something that I've never done before as I usually add the folder in /media. But I saw that it only shows about 860GB and this stuck me as odd. I know that when you buy a drive there is always a factor that is not really usable, but then I loaded up gparted. And it seems to show it as 931Gb big. Is there any reason for this loss of 90 gb? I don't really know how to search for a solution to this either.

 Thanks in advance.

---

### Post by djtecha on 2009-04-23
well i figured some of it out, apparently some of the space was being reserved for the superuser and sudo tune2fs -m 0 /dev/sda1 seemed to fix the problem by removing that space. But it does still showing that 14gb are being taken up when I use gparted opposed to the properties tab.

---

### Post by kadafi69 on 2009-04-23
I had the same problem. Apparently (depending of on the filesystem your running ext3/xfs/jfs etc) there is a certain percentage of the drive is kind put to one side as a kind of buffer and is spare for one of those moments when it goes over. Again apparently there is a way of reducing what percentage is used for this, I just dont know how to do it. Then again some file systems dont even bother doing this.

Also 1TB doesnt exactly work out to be 1000GB it is somewhere in the 900GB region. Just the way it works out.

---

### Post by gidyeo on 2009-04-23
think it's to do with the overhead / reserved blocks of ext3 filesystem. See the following article for tweaking the reserve percentage:

[http://tombuntu.com/index.php/2009/03/11/free-disk-space-by-reducing-reserved-blocks/](http://tombuntu.com/index.php/2009/03/11/free-disk-space-by-reducing-reserved-blocks/)

More on tune2fs:
[http://linux.about.com/library/cmd/blcmdl8_tune2fs.htm](http://linux.about.com/library/cmd/blcmdl8_tune2fs.htm)

---

### Post by dE_logics on 2009-04-23
> **kadafi69 said:**
> Also 1TB doesnt exactly work out to be 1000GB it is somewhere in the 900GB region. Just the way it works out.

Its 1024GB.

I dont know but in windows there's some reserved space for the recycle bin...may be reducing its size will help.

---

