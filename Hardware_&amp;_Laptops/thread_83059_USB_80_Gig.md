---
title: "USB 80 Gig"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by Joeybob on 2005-10-27
i have a 80 gig USB drive and it was formatted with windows and now i cant save to it since Ubuntu thinks it is an write only drive if anyone can help that would be GREAT thx

---

### Post by Emerzen on 2005-10-27
If it was formatted w/ Windows it is most likely in the NTFS file format or, if an older version of Windows, FAT32.  If you want to keep the file format in NTFS, then search the forums for "write NTFS" which should be fruitful.  If it's FAT32, then Ubuntu can write to it, but you have to have the correct permissions.

Ideally, you could reformat the drive in a native Linux format such as ext3 or ext2, etc...  If you go this route, I don't believe you'll be able to plug it in to a Windows box though.  The best option for a drive that both Linux and Windows need to read write to, is FAT32.  

Lemme know what direction you want to go and I can provide more details.

---

### Post by Joeybob on 2005-10-27
ok thx now i really need fat32 since i use windows 2000 at school and i use Ubuntu at hoime so how would i go about formatting the drive fat 32 style

---

### Post by Emerzen on 2005-10-27
Hook up the drive, install the either 'qtparted' or 'gparted' from Synaptic.  Open either program and select the drive.  Then under the actions menu select reformat.  A box should appear asking which format to apply, choose FAT32.

---

### Post by Emerzen on 2005-10-27
One note, you cannot write single files greater than 4GB in FAT32.  I don't know if this would be a problem for you, but some DVD movies, for example, cannot be copied at once to the drive.

---

### Post by Joeybob on 2005-10-27
ok thx a whole lot yah the 4 gig thing wont be a problem for me im not that active on this hd

---

### Post by Joeybob on 2005-10-27
ok now i cant find those packiages on synaptic

---

### Post by Emerzen on 2005-10-27
Do you have Universe and Multiverse added to your repositories?

---

### Post by Emerzen on 2005-10-27
Here's my complete sources list:



deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse universe main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted



##the antesis repo's are for Ubuntu packages that cannot be officially supported and the wine repo is for...wine.

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/

---

