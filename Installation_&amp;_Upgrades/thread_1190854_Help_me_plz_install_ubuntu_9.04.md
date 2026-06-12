---
title: "Help me plz install ubuntu 9.04"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by cnand on 2009-06-18
Hi i would like a help here how to overpass this problem.
So i have a hard disk with 3 partitions
1st is 30gb and has windows in it
2nd and 3rd are equil gb to each other (65gb each) and have my music and basically all of my life in them.
So what i would like to do is, to install ubuntu 9.04 to the first partition and delete windows.When i tried to install em i had to do some steps from 1 to 7.At the 4th step i stuck, cause thats the part that i have to choose where or how to install ubuntu by using the whole hard disk or by making partitions.I cant make a backup of the 2nd and 3rd partition and i want em as they are.
Is there anyway that i can delete windows and install ubuntu in the partition that windows are at the moment and not overwrite the other 2 partitions?
Thank you in advance.

---

### Post by Sef on 2009-06-18
1. **Back up** your **data**. 

2) You need to do a manual partition.  

2a) Delete the windows partion.

2b) do new partition (Set up as extended/logical.)

2b1) hold back on gigabyte for swap (needed if you are going to do suspend/hibernate)

2b2) set Linux partition as root. (should be default)

2b3) use default file system - ext3

2b4) set to boot

2b5) repeat 2b for one gigabyte and set up swap. (instead of ext3, set to swap)

3) Hope this make sense..Am a bit tired now.  If you do not understand something, please state what you don't understand, so you can be clear on what needs to be done.

---

### Post by presence1960 on 2009-06-18
Prior to installing a new OS one should read and become familiar with what it is they are going to do. Sef is right on the money- select manual at the prepare disk space window of the partitioner.

Here are a few links for you to peruse:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for a downloadable pdf Ubuntu Pocketguide which BTW has an excellent section on installation.

**If you don't want to lose your data BACK UP!** That is an absolute must because although partitioning and install operations usually work error free just remember that there is always a chance that something can go wrong. Don't be the one caught with your pants down and on here whining that you lost your data. BTW didn't you say your life was on that data partition. I would suggest you back it up. BTW if you jump out of a plane with a parachute it is *suggested* that you pull the cord. The choice is yours.

---

### Post by cnand on 2009-06-19
thnx a lot guys i will just buy a new hard drive and intsall ubuntu there.Thanks again for your help and for your time.

---

### Post by presence1960 on 2009-06-19
> **cnand said:**
> thnx a lot guys i will just buy a new hard drive and intsall ubuntu there.Thanks again for your help and for your time.

if you are buying a new hard disk because you need more space that is great. Hopefully you aren't buying it to avoid learning how to partition because eventually you are going to have to learn that.

Either way good luck!

---

