---
title: "REpartioning dual boots sytems"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by seantm on 2008-01-15
Hello all,

I have a what may be an unusual quesiton related to a dual boot system.  I want to do is RE-partion the size of my Windoze XP partition-- downsize it actually --make it smaller, and then Increase my Gutsy partition size. 

I have a relatively small hard drive (80GB)  and right now the Gutsy partition has only 25 gb -windoze has the rest -I'd like to reverse this 

---I' want and need more for my Gutsy and so I'd like to RE--partion and give Ubuntu the Lion's share of the drive... MS is used widely at work so I need a fraction of it for some minor lan based apps at the office...

Is it possible for me to do this???  Repartion without having to trash everything and start from scratch --ie, reinstall both of the entire operating system(s) ???  If so how? 

Any tips or advice would be greatly appreciated. TIA!!!   ~Sean

---

### Post by meindian523 on 2008-01-15
Hmm,defrag the XP partition a few times(2-3) and then resize using Disk Management(if possible,I don't remember whether XP has a resize option in Disk Management) or GParted(otherwise).Then you can grow your Gutsy partition to occupy the newly formed unallocated space(again,using GParted)

---

### Post by meindian523 on 2008-01-15
please don't blindly guess and mislead with or without intent.

---

### Post by logos34 on 2008-01-15
adept is right--only in Vista can you use the disk management tool to shrink windows partition.  So you'll have to use Gparted.  Get the latest (0.3.4) GParted live cd.  Because if this is a typical setup (ubuntu after windows), then you'll be expanding ubuntu root **to the left** into the freed space.  (IIRC only the latest Gparted allows you to drag the left partition boundary).

Make sure to defrag like they say above.  You may even need to temporarily disable swap and hibernation.  ([see this]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html"))

---

### Post by dark_phantom on 2008-01-15
I've been thinking of doing this on my laptop as well.  I think I will give this a try, use partition magic to shrink XP and then use GParted to grow Ubuntu.  This should work, right?

---

### Post by Omnios on 2008-01-15
I found a really good set up a long time ago though I used a 120G drive to do this. 

 Anyways I had a XP partition, my Ubuntu partition and also a My documents/Lin Documents drive that is shared with both XP and Ubuntu. Right now I use a fat32 format as there are reliability problems with Linux writing to ntfs and you may end up with corrupt files for ntfs when writing.

 I am also playing around with a new set up but have not tried it yet that consists of a XP partition a Ubuntu partition and I am going to play around with using the ext3 format for the file system and using a ext program in windows to mount  it as the document drive and  also change my home mountpoint to the same partition. As this is not a new install but rather a change I am going to have to research this a bit before I try it.

---

### Post by meindian523 on 2008-01-16
defrag +1.
backup +2.

I forgot to mention this,but BACKUP,BACKUP,BACKUP is the holy grail when messing with partitions,that takes care of the immovable files adept is talking about.

---

### Post by gfowler on 2008-01-16
> **seantm said:**
> Hello all,

I have a what may be an unusual quesiton related to a dual boot system.  I want to do is RE-partion the size of my Windoze XP partition-- downsize it actually --make it smaller, and then Increase my Gutsy partition size. 

I have a relatively small hard drive (80GB)  and right now the Gutsy partition has only 25 gb -windoze has the rest -I'd like to reverse this 

---I' want and need more for my Gutsy and so I'd like to RE--partion and give Ubuntu the Lion's share of the drive... MS is used widely at work so I need a fraction of it for some minor lan based apps at the office...

Is it possible for me to do this???  Repartion without having to trash everything and start from scratch --ie, reinstall both of the entire operating system(s) ???  If so how? 

Any tips or advice would be greatly appreciated. TIA!!!   ~Sean

My suggestion would be to get Gparted LiveCD iso, burn it, boot up the LiveCD and do exactly what your want, resize your XP and Gutsy partitions.  Has a nice GUI interface that is very intuitive.  Disclaimer, depending on the size of your partitions, this may take some time to finish.

The link:  [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Jerry

---

### Post by seantm on 2008-01-17
Hi all and thanks to everyone!  --For those asking about the outcome to this tech task--I haven't had chance to apply the ample tips I'm getting -maybe this weekend---i'll be sure to post the results once I try though-- TAFN ~S

---

