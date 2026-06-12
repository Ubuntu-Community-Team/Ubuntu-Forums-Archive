---
title: "I Lost All My Data while installing Ubuntu, And I want it Back!"
date: 2008-09-12
forum: General Help
---

### Post by iampriteshdesai on 2008-09-12
I installed Ubuntu using guided partition to install it in C: drive, but ubuntu erased both C: and E: drive to install it. I have lost tons of mp3's, games and movies. I have lost all my photos of vacation, myself and many memories. I want them back. Plz help me. Anything which will help me get my data back!
Plz!

---

### Post by cariboo on 2008-09-12
Just to check a few things before trying to recover your data could you please post the output of the following command. In a Applications-->Accessories-->Terminal type:

```
sudo fdisk -l
```

This will show a listing of all your drives and partitions.

Jim

---

### Post by iampriteshdesai on 2008-09-12
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeccaecca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9733     3229065    5  Extended
/dev/sda5            9332        9733     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f4fd0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4869    39110211    7  HPFS/NTFS

---

### Post by ikt on 2008-09-12
...........

Data Recovery Software is what I'd be looking for.

Why were you installing it over the top of your drive with windows on it? If you wanted to install in windows sticking the ubuntu cd in while windows is active will give you the option to safely install ubuntu and have windows not go anywhere.

---

### Post by SunnyRabbiera on 2008-09-12
yeh looks like you wiped off windows, I did that too during my first attempts.
Sorry for your loss, I know how it feels.

---

### Post by oilchangeguy on 2008-09-12
> **iampriteshdesai said:**
> I installed Ubuntu using guided partition to install it in C: drive, but ubuntu erased both C: and E: drive to install it. I have lost tons of mp3's, games and movies. I have lost all my photos of vacation, myself and many memories. I want them back. Plz help me. Anything which will help me get my data back!
Plz!

data recovery is very expensive. it goes without saying that you should always, always back up your data, BEFORE doing somthing like this. and why would you not have a back up of this important data anyway? hard drives die everyday. as another poster has said, sorry for your loss.

---

### Post by iampriteshdesai on 2008-09-12
I only have 2 drives mate.

---

### Post by aysiu on 2008-09-12
> **oilchangeguy said:**
> data recovery is very expensive.  Actually, data recovery is very cheap.

You can even use the Ubuntu CD to do it. Here's a guide:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by Cresho on 2008-09-12
I did the same thing loosing almost 500 gb of data.  What I did was use a software that enabled the lost partition.  I did not look for lost files, the software undeleted the partition and left everything in tact.  What you must not due is try to create a partition over a lost one.  Just leave the drive alone!!!!  Leave it alone until you can recover it.  If you try doing something to it, it will write and you will loose vital information.

what i used was a program called partition doctor.

[http://www.ptdd.com/](http://www.ptdd.com/)


the software scans your hardrive and tells you what lost partitions you have.  THen it gives you a choice.  It was a bit difficult figuring out what I had to choose since it also brought up older lost partitions so I just guessed...I'm just warning you here.

---

### Post by aysiu on 2008-09-12
> **Cresho said:**
> I did the same thing loosing almost 500 gb of data.  What I did was use a software that enabled the lost partition.  I did not look for lost files, the software undeleted the partition and left everything in tact.  What you must not due is try to create a partition over a lost one.  Just leave the drive alone!!!!  Leave it alone until you can recover it.  If you try doing something to it, it will write and you will loose vital information.

what i used was a program called partition doctor.

[http://www.ptdd.com/](http://www.ptdd.com/)


the software scans your hardrive and tells you what lost partitions you have.  THen it gives you a choice.  It was a bit difficult figuring out what I had to choose since it also brought up older lost partitions so I just guessed...I'm just warning you here.
Yes, if it's just the partition table that's been lost, there's also another program called [GPart](http://www.stud.uni-hannover.de/user/76201/gpart/) that guesses partition tables.

If, however, the drive has actually been reformatted, data recovery may be the way to go.

Either way should not be expensive. Ubuntu has free tools available in either case.

---

### Post by gaussian on 2008-09-12
> **iampriteshdesai said:**
> sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeccaecca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9331    74951226   83  Linux
/dev/sda2            9332        9733     3229065    5  Extended
/dev/sda5            9332        9733     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5f4fd0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4869    39110211    7  HPFS/NTFS

Are you sure you really lost the data? The output here seems to indicate you having a separate 40G hard drive with a windows partition. 

What happens if you boot into ubuntu and open the terminal (Applications-Accessories-Terminal) and type in the following:

```

mkdir temporary
sudo mount -t ntfs /dev/sdb1 temporary
ls temporary

```

After the second line it should ask for your password. Do you see any file/directory names that would seem familiar? Do you get an error message?

---

### Post by Cresho on 2008-09-12
Device Boot Start End Blocks Id System
/dev/sdb1 1 4869 39110211 7 HPFS/NTFS

this tells me different but he says he lost his data!  Like you said, maybee his partition is not mounted :popcorn:  He isnt being specific about where he lost the data from what partition though.  he does say he lost c and e drive and I am going to assume d drive is the cd.

---

### Post by iampriteshdesai on 2008-09-13
Well I have 2 drives. One is of 80 Gb and another of 40 Gb. The precious 2 C: and E: drives were residing on the 80 Gb HD.That disk was partitioned. I didnt knew that and happily used the "Erase entire disk" and Ubuntu wiped off both the drives.
Here is the output from 
mkdir temporary
sudo mount -t ntfs /dev/sdb1 temporary
ls temporary:

21 Easy Hacks to Simplify Your Life   Zen Habits_files
21 Easy Hacks to Simplify Your Life   Zen Habits.htm
C&C++
CDlerim
Directorate of Technical Education,Maharashtra State,Mumbai.htm
Dragon
far cry
FIFA08
firefox3selecttext-thumb.gif
Games
hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php_files
hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php.html
HALF LIFE 2
Infernal
int2.jpg
int3.jpg
int.jpg
ip.txt
Iron Maiden-Live After Death disc 1&2
Judas Priest -Ram It Down
Movies
Mr Beans
opera6.adr
Prodigy
RECYCLER
Rocky
Screenshot-1.png
Screenshot-Disk Usage Analyzer.png
Screenshot-Softwares - File Browser.png
speedrd.exe
System Volume Information
Tintin
tyit0809
VIDEO_TS
winestripe__classic_1.5_look_for_firefox_2.0_-1.2.2-fx-linux.jar

---

### Post by iampriteshdesai on 2008-09-13
Well I have 2 drives. One is of 80 Gb and another of 40 Gb. The precious 2 C: and E: drives were residing on the 80 Gb HD.That disk was partitioned. I didnt knew that and happily used the "Erase entire disk" and Ubuntu wiped off both the drives

---

### Post by kokkus on 2008-09-13
Seams like the only way you can get back your MP3s are with PhotoRec that comes with testdisk.
Run PhotoRec on both your HDs and see how many of your MP3s you can get back. Then you have to find a program to auto rename your mp3s to the artist and title info inside the files. I don't know any for linux.

---

### Post by Sef on 2008-09-13
[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") can repair your partition.  It is best not to use your hard drives until after you attempt fix your system. (Hopefully it will be successful.)

---

### Post by Martje_001 on 2008-09-13
> **iampriteshdesai said:**
> Well I have 2 drives. One is of 80 Gb and another of 40 Gb. The precious 2 C: and E: drives were residing on the 80 Gb HD.That disk was partitioned. I didnt knew that and happily used the "Erase entire disk" and Ubuntu wiped off both the drives.
Here is the output from 
mkdir temporary
sudo mount -t ntfs /dev/sdb1 temporary
ls temporary:

21 Easy Hacks to Simplify Your Life   Zen Habits_files
[..]
winestripe__classic_1.5_look_for_firefox_2.0_-1.2.2-fx-linux.jar
Looks like you have your data back.. Run the commands again from a live cd and look in your **home-folder** (Location --> Personal Folder) and then in the folder **temporary**.

---

### Post by iampriteshdesai on 2008-09-13
The folder and file names you can see are from the other drive. I had wisely unhooked it from the system while installing Ubuntu, so its contents are safe. It was the other E: drive which got Lost.

---

### Post by DrMelon on 2008-09-13
Next time you try a large undertaking like this one, remember to back up things onto CD's or online storage. Perhaps that should be part of the installation of Ubuntu...if you were able to set up a domain or had some CD's Ubuntu could backup all your stuff during the installation phase.

---

### Post by patrickfromspain on 2008-09-13
**** happens. A drive may contain one or more partions. If you say erase the whole drive... goodbye. It's not ubuntu's fault, but yours.

Good luck in recovering data.. I guess it won't be that easy.

---

