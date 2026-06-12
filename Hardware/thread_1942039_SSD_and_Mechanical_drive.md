---
title: "SSD and Mechanical drive"
date: 2012-03-16
forum: Hardware
---

### Post by xtiano77 on 2012-03-16
I have been looking around for information on how to install two hard drives in my Ubuntu box. I am would like to know if it is possible to install a SSD for operating system and a mechanical for the files. That said, how large would the SSD need to be to accomodate Ubuntu 11.10 and later versions. Also, what would the format specs be for the mechanical drive (i.e., jumpers, FAT, etc.). Thanks in advance.

---

### Post by Basher101 on 2012-03-16
well, depends how you use Ubuntu. I think 32 gigs should be enough, but as i said, that would be enough the way I use it..

as fot the specs, you should take a 5200 RPM drive, and the connection (IDE/SATA) depends on what motherboard you want to install the hard drive to. Just check the specs of the machine and it should tell you what kind of connector it uses (most computers use SATA, SATA II nowadays).

---

### Post by bryanl on 2012-03-16
I use root and home partitions with the swap as a file on the root. I find that a 16 GB root provides plenty of room for the system.

On a 128 GB SSD on my laptop, I allocate 16 GB to / - 55 GB to Windows - 43 GB to /home - and 13 GB for Ubuntu+1 (Precise) testing and evaluation.

---

### Post by javierc on 2012-03-16
Well am my windows 7 i been using about 40GB and might be going on to 60GB because of the programs that I use and some games that I installed and i have all my files in a USB 3 Hard Drive, its a laptop so i can't install a second Hard drive and by the way am using a 128GB SDD from crucial, pretty cheap and i better keep the receipt in case anything goes wrong with the SDD, because older SDD just brake too soon.

So it really depends how many application your installing on your ubuntu.

---

### Post by xtiano77 on 2012-03-16
I appreciate all the responses. I was thinking about a 60GB SSD from Crossair or OCZ so Ubuntu or any other distro has room to to perform. As far as the applications, well I am not a gamer or anything like that, I ocassionally download videos from Youtube and other sites as well as music. I guess the hardest thing on the hard drive will be the music and some occassonal Java and PHP code for a few web sites.

As I wrote on the original post, my main concern was the installation of the second drive because most of the stuff I've read about it shows a bunch of configuration and bash script changes in order to get the second drive to be recognized and to mount as far of the booting process. Another thing is that I am considering setting up my current Linux box with Windows 7 and giving it to my wife and dauthers, then purchasing a new box with the two hard drives (SSD and mechanical) along with an i7 intel chip in order to maximize speed.

That said, I guess what I want to make sure is that once installed, the second drive can be easily configured (wihtout minimal bash editing or perhaps even via the Disk Utility application) and setup to auto-mount as part of the booting process.

---

### Post by Jagoly on 2012-03-18
I've got a 60gb corsair force 3 SSD, a 1tb segate barracuda 7200rpm, and an old 320gb seagate barracuda 7200rpm. But I've got them set up in what is most likely an unnecessarily complicated configuration.

I have both / and /home mounted on the SSD, roughly 25gb for / and 35gb for /home. I then have the 1tb drive mounted as /storage and symlink large folders all over the ssd to places in /storage. So documents, Videos, music, the apt cache, playonlinux's resources and wineprefix folders, virtualbox VMs, .minecraft, and probably a few other things I've forgotten. This is so that all of the user specific settings and resources are on the SSD for speedy access times. But, if you not a fan of setting everything up manually exactly how you want (I love this sort of thing) than mounting /home on the big drive is fine.

I have swap as a 20gb partition (WAY more than I need, but it suffices if I ever double my RAM to 16gb, and 20 is a rounded number. I like rounded numbers XD).

The 320gb drive is just salvaged from my old desktop, It is seperate and contains ubuntu 12.04 and arch linux at the moment.

At the moment, according to the system monitor, I have used:
7gb out of 24gb of /
3.3gb out of 31gb of /home
251gb out of 897gb of /storage

when I update to 12.04 I'll be switching the / and /home partitions, as I've ended up using much more space there.

If you carefull with space, 60gb is heaps for ubuntu.

---

