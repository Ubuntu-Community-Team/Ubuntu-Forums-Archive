---
title: "External Hard Drive Problem"
date: 2008-05-26
forum: Hardware
---

### Post by TXJBAR on 2008-05-26
I am a beginner to the Linux OS. I bought a new hard drive and did a fresh Ubuntu install on it. On my other hard drive I run Window XP Pro. Now, I use an external hard drive for backups mainly, but since I had all my music files on it, I decided to plug it into ubuntu and transfer all my music so I could listen to my music using rythmbox (i believe thats the name). All the music on the hard drive however could would not open, the folder it was in on the external hard drive was empty (i got a message saying that the files in that directory could not be opened). I am use to "safely removing" the ext. hard drive (in Windows) so i tried to do the the same in ubuntu by right clicking the icon on the desktop and selecting unmount. I learned that was not the same. Now the my external hard drive will not be recognized by either my ubuntu or windows hard disks and on top of that for some reson or another i lost about 2/3 of my music files on my windows drive. All the directories to my music files are there but the music files themselves are not (Lucky I have all the music files backup on my laptop as well). My questions:

Why would'nt ubuntu recogvize my music files and how do i get ubuntu to do so?

How can i get my hard drive recognized again?

What in the world happened to my music files on my windows drive?

---

### Post by nebben11 on 2008-05-26
Welcome to Ubuntu we are happy to help with problems

1. > Installing codec on Ubuntu 8.04
System> Administration > Synaptic Package Manager and install all gstreamer 

Install w32codecs and libdvdcss2
Support for WMV, RealMedia and other formats has been bundled into the w32codecs package. This package is not available from the Ubuntu repositories due to licensing and legal restrictions.
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
Then, add the GPG Key using the following commands
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update

For i386 Users install Codecs using the following command
sudo apt-get install w32codecs libdvdcss2

2. mount the ext hdd > sudo mkdir /media/External
sudo mount -t <filesystem> /dev/<insert device name here (ie. sdb1) /media/External

3. thats windows falt not ubuntu's

---

### Post by TXJBAR on 2008-05-26
Im using Ubuntu 7.10, do i still use the same procedure as you listed in 1. Also, for the command you listed in 2.:

sudo mount -t <filesystem> /dev/<insert device name here (ie. sdb1) /media/External 

How do i find out the device name because when i plug the drive in, it is not picked up, not even by the partition editor?

---

### Post by nebben11 on 2008-05-26
#1 yes
#2 MOST ext hdd use vfat also known as fat some use ntfs I would do a search on google and find out

---

### Post by TXJBAR on 2008-05-26
What should i put in for the drive name, as i said not even the partition editor would pick it up?

---

### Post by nebben11 on 2008-05-26
I would use see if sda1 works if not try sdb1

---

### Post by nebben11 on 2008-05-26
here's a tut about mounting hdd's in linux [http://www.gnulinuxclub.org/index.php?option=com_content&task=view&id=38&Itemid=31](http://www.gnulinuxclub.org/index.php?option=com_content&task=view&id=38&Itemid=31)

---

### Post by TXJBAR on 2008-05-26
I found out that my ext HDD is and ntfs filesystem. I plugged my hard disk drive into Ubuntu and it somehow recognized it again without doing the steps in (2). I am supposing this means it is mounted again. It did all the steps in (1), but when i go in to the ext HDD and try to open the directory with my music files it still does not display any of my music files (mainly mp3's) however all my pictures are there. Why is this?

Another question also, when i am ready to unplug my ext HDD from the system, what steps should i proceed to saftley remove it?

---

### Post by nebben11 on 2008-05-26
right click on the file system icon (you ext hdd icon) and click unmount

---

