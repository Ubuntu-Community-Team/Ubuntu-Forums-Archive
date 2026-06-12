---
title: "I need help partitioning External HD for Windows XP."
date: 2009-09-12
forum: Hardware
---

### Post by Hero_Of_Time on 2009-09-12
I am trying to partition my external hard drive (Western Digital My Book) so I can install Windows XP on it.  I tried several times with my standard Ubuntu Partition Editor,but it either cannot or refuses to partition it in NTFS format which is required for Windows XP.  If possible, what is the best way to format the My Book to NTFS format?

Thank You for any advice

---

### Post by rob-ward on 2009-09-12
Doesn't the windows installer let you partition a drive?

If not you should be able to do it under ubuntu using gparted, you will however need to install the ntfs tools, you will have to search for them under the package manager as I can't remember what they are called, or someone else may know????

---

### Post by BlueerSkies on 2009-09-12
> **Hero_Of_Time said:**
> I am trying to partition my external hard drive (Western Digital My Book) so I can install Windows XP on it.  I tried several times with my standard Ubuntu Partition Editor,but it either cannot or refuses to partition it in NTFS format which is required for Windows XP.  If possible, what is the best way to format the My Book to NTFS format?

Thank You for any advice



Bismillaah.   Peace, Hero_Of_Time.      


Synaptic Package Manager: ubuntu 9.04

ntfsprogs  v2.0.0-1ubuntu2  tools for doing neat things

ntfsdoc   0.5-1   documentation re: NTFS partitions format
 

Additionally, I don't know how you should go about it, but  XP's partitioning software will partition your external hard drive.  Perhaps you have another pc that you can install XP, on.


BlueerSkies

---

### Post by Hero_Of_Time on 2009-09-12
Thank you for everything.  I tried using the Windows Partitioning agent, but the Windows installation complained it was not Windows compatible.  I will give this one last try and cross my fingers.[-o<

---

### Post by Hero_Of_Time on 2009-09-12
](*,)](*,)](*,)](*,)


[SIZE=5]This is not a Windows compatible partition.
I HATE WINDOWS!!!!

[/SIZE]](*,)](*,)](*,)](*,)

---

### Post by David-IT on 2009-09-12
hmm windows is not to bad try this. get your ubuntu live cd load it up with your external drive connected to your pc then go to system>administrator>Partition Editor application. Then Select the hard drive you wish to partition in the pull-down menu on the top right corner of Partition Editor's main screen. Then click delete to delete the current partition / file system then click new then a window will appear just click ntfs on the file system and when you are finished save your changes with the apply button and bam then just restart your pc and have fun with the partition manager in wondows :D remember: Under Ubuntu Linux's drive-naming scheme, the name of your main hard drive is /dev/sda. Secondary and external hard drives are named /dev/sdb, /deb/sdc, and so forth. Ubuntu Linux allows you to partition your hard drive graphically or textually. The graphic process is simpler and easier to understand, but less sophisticated. The manual process is more complicated, but provides greater control of the type and size of your partitions.

---

### Post by Hero_Of_Time on 2009-09-12
Can I unmount and resize my main hard drive without having to erase everything on my hard drive first?
:popcorn:

---

### Post by rob-ward on 2009-09-13
You can do this from a ubuntu live cd, however before you do that I would backup any importnat data as it isn't always 100% reliable. You should also defragment your windows drives prior to resizing them as well, if not windows gets in a bad mood.

---

