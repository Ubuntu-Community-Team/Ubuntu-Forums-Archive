---
title: "how to repartition HD for linux while keeping the windows recovery files"
date: 2010-01-11
forum: Hardware
---

### Post by angko on 2010-01-11
i bought a new 2.13GB penrin toshiba satelite L505-10P laptop. it has a
500GB harddisk with 3 partitions in it, the 1st is a the 400mb recovery
partition, the 2nd a 232gb NTFS with a 64bit french win7 home premium in
it, the 3rd is a 232GB NTFS contains recovery files: msdia80.dll, 
R11461FR.tag N a directory: HDDRecovery contains several subdirectories.
i want to repartition the HD but i'm new to toshiba and to win7 n 64bit 
systems. i'm planning to do:

1. copy the recovery files in the 3rd partition to a removable media
2. shrink the 1st partition to the minimum possible. should i? how many
   MB?
3. shrink the 2nd/win7 partition to maybe 100GB (any advise?)
4. del the 3rd partition
5. make an extended partition in the place of the 3rd
6. make some logical partitions in it, with specifics drives for:
   a. general data
   b. music n multimedia (actually i have nearly 70GB of music, plus
      some videos/records)
   c. backup where i'm gonna put the recovery files from the former 3rd
      partition
   d. a linux swap (how big? i have 4GB of RAM)
7. make the 4th primary partition for 1 or 2 distro: ubuntu or kuliax
   (an indonesian debian derivee suited for IT learning n programming)

my questions are:
1. what i know is that a HD can only contain 4 primary partitions. 
   please CMIIW
2. if i proceed like that, will the recovery process be always 
   fonctional? will the recovery image not be alterated? can i move
   freely the contains of the former 3rd partitons into another one? i'd
   like to keep them cos they're to keep the genuine windows privileges
   in case of reinstallation.
3. i've always use gparted CD for partitioning, will it be good to
   manipulate the 64bit win7 created partition?
4. will the GRUB not alterate the recovery process? will the recovery
   still be accessible by pressing F8 while booting?
5. i want to have the 2 linux distros installed, can I? what's the best
    way to proceed? how should i repartition my 500GB HD?
6. any further info n advises please.
 
thank you very much

---

### Post by lyall on 2010-01-13
Hi
I got my son a new HP DV7 laptop for Christmas and checked HP site about buying a recovery CD/DVD. They want over $16.12 for the DVD.  It is money will spent.

On their site they explain how to create your own recovery DVD for
see the following link
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00810334&lc=en&dlc=en&cc=us&lang=en&product=4041781#]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00810334&lc=en&dlc=en&cc=us&lang=en&product=4041781#")

Yes I know it is from HP, by you should be able create your own DVD for the recovery form toshiba.  check their web web for support and you should found out how they say to create your own recovery DVD


You should a recovery CD/DVD just encase the hard drive goes bad, whcih they all do sooner or later.

If you got a good copy of the recovery CD/DVD ( by making your own or buying one) then you be able to install Ubuntu on the full hard drive if you do not want to use Window 7 at is time.

See others on the forums how they install Ubuntu on Windows or Windows on Ubuntu.  I am not sure which way is the best.

Good luck and have fun learning

---

### Post by angko on 2010-01-24
thank you, Iyall. tried to partition with partitionwizard cos they say it's an excellent tool that can handle 64bit windows7 partition. but then my laptop couldn't boot. fortunately i'd made my recovery CD b4. maybe the problem is with the 64bit thing, or if i had used gparted instead maybe all was just fine.  still will try to dig again, but due to works will wait until february  to try to repartition again.

---

