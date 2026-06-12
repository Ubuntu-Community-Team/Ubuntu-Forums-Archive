---
title: "[hardy] apt-get update from harddisk error..."
date: 2008-10-19
forum: General Help
---

### Post by l3modz on 2008-10-19
It first time I using Ubuntu Hardy, and I don't now how to install/remove/update of my Package

I've 5 DVD repository (file ISO), and I want install amarok, cause as default  Ubuntu not play *.mp3

Then I copy all ISO to my harddisk and want update from local cause I dont have Internet connection everyday...

here I done and follow from other site tutorial...
First I've mount the ISO file
```
#mount -t iso9660 -o loop /media/OTHERS/ubuntu-8.04-repository-i386-1_contrib.iso /media/DOCUMENTS/ubuntu/repo1
#mount -t iso9660 -o loop /media/OTHERS/ubuntu-8.04-repository-i386-2_contrib.iso /media/DOCUMENTS/ubuntu/repo2
#mount -t iso9660 -o loop /media/INSTALLER/ubuntu-8.04-repository-i386-3_contrib.iso /media/DOCUMENTS/ubuntu/repo3
#mount -t iso9660 -o loop /media/INSTALLER/ubuntu-8.04-repository-i386-4_contrib.iso /media/DOCUMENTS/ubuntu/repo4
#mount -t iso9660 -o loop /media/INSTALLER/ubuntu-8.04-repository-i386-5_contrib.iso /media/DOCUMENTS/ubuntu/repo5


```

then I edit /etc/apt/sources.list and change my path to my harddisk external...
```
deb file:///media/DOCUMENTS/ubuntu/repo1
deb file:///media/DOCUMENTS/ubuntu/repo2
deb file:///media/DOCUMENTS/ubuntu/repo3
deb file:///media/DOCUMENTS/ubuntu/repo4
deb file:///media/DOCUMENTS/ubuntu/repo5
```

from that tutorial I must run # apt-get update
but I get error...
```
root@apt-error-laptop:~# apt-get update
Ign file: hardy Release.gpg
Ign file: hardy/main Translation-en_US
Ign file: hardy/restricted Translation-en_US
Ign file: hardy Release.gpg
Ign file: hardy/main Translation-en_US
Ign file: hardy/multiverse Translation-en_US
Ign file: hardy/universe Translation-en_US
Ign file: hardy Release.gpg
Ign file: hardy/universe Translation-en_US
Ign file: hardy Release.gpg
Ign file: hardy/universe Translation-en_US
Ign file: hardy Release.gpg
Ign file: hardy/universe Translation-en_US
Ign file: hardy Release
Ign file: hardy Release
Ign file: hardy Release
Ign file: hardy Release
Ign file: hardy Release
66% [Packages bzip2 0]
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Input/output error
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign file: hardy/main Packages
67% [Packages bzip2 0]
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Input/output error
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign file: hardy/restricted Packages
Err file: hardy/main Packages
  Read error - read (5 Input/output error)
Err file: hardy/restricted Packages
  Read error - read (5 Input/output error)
79% [Packages bzip2 0]     
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Input/output error
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign file: hardy/universe Packages
Err file: hardy/universe Packages
  Read error - read (5 Input/output error)
80% [Packages bzip2 0]
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Input/output error
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign file: hardy/universe Packages
Err file: hardy/universe Packages
  Read error - read (5 Input/output error)
80% [Packages bzip2 0]
bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Input/output error
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign file: hardy/universe Packages
Err file: hardy/universe Packages
  Read error - read (5 Input/output error)
W: Failed to fetch file:///media/DOCUMENTS/ubuntu/repo1/dists/hardy/main/binary-i386/Packages.gz  Read error - read (5 Input/output error)

W: Failed to fetch file:///media/DOCUMENTS/ubuntu/repo1/dists/hardy/restricted/binary-i386/Packages.gz  Read error - read (5 Input/output error)

W: Failed to fetch file:///media/DOCUMENTS/ubuntu/repo3/dists/hardy/universe/binary-i386/Packages.gz  Read error - read (5 Input/output error)

W: Failed to fetch file:///media/DOCUMENTS/ubuntu/repo4/dists/hardy/universe/binary-i386/Packages.gz  Read error - read (5 Input/output error)

W: Failed to fetch file:///media/DOCUMENTS/ubuntu/repo5/dists/hardy/universe/binary-i386/Packages.gz  Read error - read (5 Input/output error)

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@apt-error-laptop:~# 
```

What must I've to do to resolve this problem??? It that my ISO file corrupt ???

---

### Post by br4d on 2008-12-09
Try to check the volume of your ISO-files. 
I've had the same experience by copying dvd-iso on a FAT-Partition.

A FAT-Partition limits filesize to max 2 GB. Need a night to figure it out.:lolflag:

Hope that helps

---

### Post by l3modz on 2008-12-24
anyway thanks... for me better try Ubuntu 8.10 now :popcorn: 

Btw... can I use Intrepid Repository for Hardy, cause I've deleted all repos Hardy, and now I have Intrepid installer and repo???

and now [_I get problem with Intrepid_]("http://ubuntuforums.org/showthread.php?t=1020347")

---

