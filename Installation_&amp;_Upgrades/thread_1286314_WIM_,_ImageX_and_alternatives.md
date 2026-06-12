---
title: "WIM , ImageX and alternatives"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by gimfred on 2009-10-08
Hi,

I've been working with a corporation that is naturally only 'able' to consider MS products. As a new techy I'm being educated in 'WIM' based deployments. While they do use Ghost and other imaging software, most of the time they are taking wims and I was wondering if anyone had heard of alternatives?

From Wikipedia:
> WIM is file-based, which means that the smallest unit of information is a file. The primary advantages of it being file-based include hardware independence and unique storage of a file referenced multiple times in the filesystem tree (single instance storage).[http://en.wikipedia.org/wiki/Windows_Imaging_Format]("http://en.wikipedia.org/wiki/Windows_Imaging_Format")

Is it possible for a tar.gz to emulate this? I'd be much happier about using it if it wasn't dependent on only MS continuing the 'technology'.

---

### Post by gimfred on 2009-10-09
I've been wondering if dd and gzip would be able to produce most of the functionality of ImageX and WIMs?

I was thinking if we saved the mbr:**

```
dd if=/dev/hda of=backup-hda.mbr count=1 bs=512
```

and the various partitions:

```
sfdisk -d /dev/hda > backup-hda.sf
```,

then all that would be required is a gzip of required system files and directories... ?

The only thing I am completely blown away by is the single copy of files within the wims (Singe Instance Storage). I've seen a 630mb disk be reduced 475mb; as the disk was an install disk, I'm guessing that the files were already compressed. That makes it respectable.

P.S I've recently been begged to *ahem! sulked/cried into* return MS Windows by my wife. Not because it wasn't working, but because she didn't understand how to save to a ufd which was labeled in Dolphin... Gah. 

Long and short is that I currently don't have linux on my singular machine and can't personally try this.

---

### Post by gimfred on 2009-10-11
Seems no-one else even has a reason to comment... 

I've found out the Single Instance Storage seems to be Copy-On-Write (COW) that is in ZFS and BTRFS. 

Does anyone know a yea or nay here?

---

### Post by gimfred on 2011-02-26
Well, seems no one is curious about this. I'm going to have to try it.

---

### Post by gimfred on 2011-09-01
Just wanted to say I couldn't quite get this to work over the past 2(!) years. 

If someone has some knowledge on this it would be nice to share ... please?.

---

### Post by fmo on 2011-09-19
Hi,

I think you might want to have a look at [http://www.partimage.org](http://www.partimage.org) it provides the same kind of features as Ghost.

But I would probably go about it in a different way and use tools like kickstart with answer files to deploy linux servers.

If you want more high-end functionalities you might want to try [OpenQRM]("http://www.openqrm-enterprise.com") or [SpaceWalk]("http://spacewalk.redhat.com/").

---

### Post by gimfred on 2011-11-08
Hi fmo,

Yeah I know about them but there is a difference between partimage (ghost etc) and wim. Cloning software is block based and wim is file based. In most cases, block based cloning is superior, but occasionally file-based may have a reason to exist. 

Hence, I'm trying to solve how to make this work.

---

### Post by pandion on 2012-01-12
Hi,

It's still under developement, but FSArchiver sounds closer to what you're looking for.  It's file-based rather than block/sector-based, and supports more filesystems than ImageX.  I haven't used it, but it sounds promising.  It has been included in some bootable CDs such as the SystemRescueCD.

[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)
[http://www.fsarchiver.org/Fsarchiver_vs_partimage](http://www.fsarchiver.org/Fsarchiver_vs_partimage)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[http://www.mguhlin.org/2009/10/fsarchiver-backup-just-data.html](http://www.mguhlin.org/2009/10/fsarchiver-backup-just-data.html)

---

### Post by FalconFour on 2013-03-04
I figured I should chime in here, as WIM is kind of my... particular area, in my small corner of generally Windows-based systems. Maybe to help bridge the gap here for Linux users...

What WIM does that's unique is that it's entirely file-based, but captures a partition in roughly the same way Ghost or other partition-cloning software would do it. I use GImageX - which is an amazing UI for ImageX. It can't clone one partition/volume to another (which is a huge shame, actually - considering how it operates), but it creates "images" of file systems. That WIM contains all the information needed to not "restore" the file system - but to "apply" it to a new or existing filesystem. You basically "extract" a WIM onto a new partition. You can also browse a WIM in 7-zip since it's file-based. The key is that it restores *all* parts of NTFS as objects - like a directory with links to file IDs and the attributes of the files, the files' data itself, etc. So it can save/restore links (symbolic, hardlinks, etc), ownership, permissions, attributes, etc.. And when you restore it, it rebuilds all these links into the new file system - usually making a much cleaner system with improved performance - often "like new".

I'd be curious about a Linux alternative as well. I thought it would be tar, being "Tape ARchive", it would be for file system archiving - including links, ownership, attributes, etc. That would be a Linux equivalent to WIM, I believe...

---

