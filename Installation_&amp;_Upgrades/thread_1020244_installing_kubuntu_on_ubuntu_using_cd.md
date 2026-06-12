---
title: "installing kubuntu on ubuntu using cd?"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by jestinjoy on 2008-12-23
I tried installing kubuntu on ubuntu using kubuntu CD. But it didnt work....Please help...The method I followed is given below..........

```
**root@jestinjoy-desktop:/home/jestinjoy# apt-cdrom add**
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [27b27dcec05824d0e2cf35487540bd1a-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)'
Copying package lists...gpgv: Signature made Thursday 30 October 2008 03:58:55 AM IST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
W: Skipping non-exisiting file /cdrom/dists/intrepid/main/binary-i386/Packages
W: Skipping non-exisiting file /cdrom/dists/intrepid/restricted/binary-i386/Packages
**root@jestinjoy-desktop:/home/jestinjoy# mount /dev/cdrom**
mount: block device /dev/scd0 is write-protected, mounting read-only
**root@jestinjoy-desktop:/home/jestinjoy# apt-get install kubuntu-desktop**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kubuntu-desktop
root@jestinjoy-desktop:/home/jestinjoy# 
```
:confused::confused:

---

### Post by SuperSonic4 on 2008-12-23
Can you add the CD to /etc/apt/sources.list or sudo aptitude install kubuntu-desktop
Or just install kubuntu packages alongside ubuntu or as separate?

---

### Post by jestinjoy on 2008-12-23
First few lines of sources.lst is given below....

```
deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


```

When i tried it showed something......but there is no option to login to kde after logging out from ubuntu........the command is given below...

```
root@jestinjoy-desktop:/home/jestinjoy# sudo aptitude install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "kubuntu-desktop"
Couldn't find any package whose name or description matched "kubuntu-desktop"
The following packages will be REMOVED:
  emacsen-common{u} 
0 packages upgraded, 0 newly installed, 1 to remove and 199 not upgraded.
Need to get 0B of archives. After unpacking 147kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 117221 files and directories currently installed.)
Removing emacsen-common ...
emacsen-common: Handling removal of emacsen flavor emacs
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```

I want it in such a way that i could select KDE?GNOME while logging in....:(

---

### Post by zvacet on 2008-12-24
If you are trying to install kubuntu-desktop from live CD I don´t think it will work.You need alternate CD or download kubuntu-desktop via net.

```
sudo apt-get install kubuntu-desktop
```

---

### Post by jestinjoy on 2008-12-24
I have a very slow net connection at home..........Is there any alternate method?

---

