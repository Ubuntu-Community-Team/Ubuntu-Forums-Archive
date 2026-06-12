---
title: "installing ubuntu on secondary hd"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by Lynx Phoenix on 2009-05-30
hi all,

i've got 2 HDs on this pc, one 80gb main for xp (ntfs) and a 300gb (fat32) for storage. i want to install ubuntu on the second one as i think it would be best. i've cleared about 50gb for ubuntu on the 300gb hd and i'm defragging it so that the free space is all in one piece. i also intend to install grub on the ubuntu partition and use gag instead to boot.

i've read about installing ubuntu after xp and dual booting and i've also read about installing ubuntu alone. the thing is, i don't know exactly where my case falls into. obviously if i was installing on the 80gb drive i wouldnt need to format or anything, but what about the 300gb drive? its lighter than trying to fit two operating systems on one drive but am i risking too much without formatting?

will ubuntu still ask me if i want to dual boot if i install on a drive without xp, while i have xp installed on the pc?

i'm also thinking that perhaps i should evacuate the 300gb drive, but its a big hassle (250 gigs of stuff is alot of work...) and i'd like to at least have a way to test whether the installation might have problems with partitioning. also, should i try partitioning it beforehand? like making an solid 50gb ext3 partition for ubuntu to slice up before starting installation.

in [http://ubuntuforums.org/showthread.php?t=899222](http://ubuntuforums.org/showthread.php?t=899222) post #2 this guide mentions you should have an uninterrupted power supply etc etc if you want to resize and its making me a bit nervous. isnt resizing exactly what you do with partitioning unless you're formatting?
thanks in advance, hopefully i'll soon be ready to escape windows for good! :popcorn:

---

### Post by Mark Phelps on 2009-05-30
Your only options are to install Ubuntu inside Windows (using Wubi) and have it then installed to the second drive, or to reformat the second drive to make room for Ubuntu partitions and install it dual-boot.  Ubuntu can't install natively in FAT32 or NTFS partitions, it requires Ext3 or Ext4 partitions (among others).

---

### Post by Lynx Phoenix on 2009-05-30
can't i install ubuntu natively if i create a 50gb ext3 partition before the installation?

---

### Post by Lynx Phoenix on 2009-05-31
bump

---

