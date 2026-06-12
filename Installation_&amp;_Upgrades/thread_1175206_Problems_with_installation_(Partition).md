---
title: "Problems with installation (Partition)"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by AE000 on 2009-05-31
I'm having problems when installing Ubuntu 8.10 on a WD3200AAKS hd. I chose the guided partitioning with 100% of the hd for Ubuntu but after 5% I get an error saying that there was a problem creating the partition and it leaves me with only a 7.2Gb partition for ubuntu.
 
I'm new to this system and did not understand the options on the Manual partition.
 
Any suggestions will be appreciated.
 
Alex.

---

### Post by AE000 on 2009-06-01
After several tries the partitioning kept aborting at 5% which left me with 97% of my 320Gb hd as "free space" and 7% (7.2Gb) available to install Ubuntu so I installed it there and after the installation I upgraded to version 9.04.

I thought that I would be able to use the remaining 97% for my personal files but Ubuntu doesn't seems to "see" that part of the HD.

Any suggestions on what I can do to use this portion of my HD? Is it ok to keep ubuntu on 7.2Gb only?

My HD is a 320Gb Western Digital (WD3200AAKS).

Thanks!

Alex.

---

### Post by lake54 on 2009-06-01
Try going to System > Admin > Partition Editor, and create a partition in the unallocated space (best to use the ext3 format).

Ubuntu should then be able to see that space, but your /home/ directory won't be on it - you'll have to place files there manually.

James

PS - you *can* move your home dir there, but I'm not sure how you do it - try either on the wiki, or someone will reply back here soon!

---

### Post by raymondh on 2009-06-01
Hello Aeooo,

If OK with you, kindly post back a screenshot of gparted as well as

```
sudo fdisk -l
```

(small L, not 1).

It'll help us get a better picture of what your HD looks like at the moment.

Thanks,

---

### Post by AE000 on 2009-06-01
> **raymondhenson said:**
> Hello Aeooo,

If OK with you, kindly post back a screenshot of gparted as well as

```
sudo fdisk -l
```(small L, not 1).

It'll help us get a better picture of what your HD looks like at the moment.

Thanks,

Raymond, here's the output of that command (sorry, I couldn't keep the columns aligned):
[FONT=Palatino Linotype]
[/FONT] [FONT=Trebuchet MS]Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000d0efd

Disposit.      Inicio         Comienzo           Fin               Bloques       Id      Sistema
/dev/sda1         *                           1                 37974      305026123+     83       Linux
/dev/sda2                               37975              38913           7542517+       5        Extendida
/dev/sda5                                37975             37976                 16033+      82      Linux swap / Solaris
/dev/sda6                                37977              38866            7148893+      83       Linux
/dev/sda7                                38867             38913               377496        82       Linux swap / Solaris[/FONT][FONT=Courier New]

Here's the gparted screenshot (*desconocido=unknown;))

[/FONT]

---

### Post by raymondh on 2009-06-01
> **AE000 said:**
> Raymond, here's the output of that command (sorry, I couldn't keep the columns aligned):
[FONT=Palatino Linotype]
[/FONT] [FONT=Trebuchet MS]Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000d0efd

Disposit.      Inicio         Comienzo           Fin               Bloques       Id      Sistema
/dev/sda1         *                           1                 37974      305026123+     83       Linux
/dev/sda2                               37975              38913           7542517+       5        Extendida
/dev/sda5                                37975             37976                 16033+      82      Linux swap / Solaris
/dev/sda6                                37977              38866            7148893+      83       Linux
/dev/sda7                                38867             38913               377496        82       Linux swap / Solaris[/FONT][FONT=Courier New]

Here's the gparted screenshot (*desconocido=unknown;))

[/FONT]

Hello Alex,

Just got through re-reading your original post and realized that you wanted ubuntu as the sole OS on your HD.  From what I understood ... you have trouble getting past the installation portion of the liveCD ... i sthis correct?

Let's try a different approach if you want.  We will try to erase everything.  Are you able to download gparted and burn that into a CD (note, read the warning notes on the download page and see if it applies to your machine)

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Boot into that and use it to delete the entire HD.  Delete from the right most partition.  After leaving it unallocated, right click > new and format into ext3.  Once succesfull,  Quit application and eject CD.

Now boot into the ubuntu liveCD and point the installer to that new partition.

A lo mejor, your problems may stem from a bad/corrupted LiveCD.  Did you check it for defects?

Good luck,

---

### Post by AE000 on 2009-06-01
I'll try the gparted tonight, later I'll post what happened.
I got the Ubuntu CD by mail (to my surprise because I never thought it would ship to Mexico within 1 week only) so I don't think that it was corrupted. Anyway, I'm downloading version 9.04 and I'll check for errors prior to installing.

---

### Post by gordintoronto on 2009-06-01
A small suggestion: allocate a small partition (such as 30 GB) as "root", then the swap partition (twice as big as your memory) and the rest as "home".  This could make things easier when it's time to upgrade versions.


> **AE000 said:**
> I'll try the gparted tonight, later I'll post what happened.
I got the Ubuntu CD by mail (to my surprise because I never thought it would ship to Mexico within 1 week only) so I don't think that it was corrupted. Anyway, I'm downloading version 9.04 and I'll check for errors prior to installing.

---

### Post by AE000 on 2009-06-02
> **raymondhenson said:**
> Hello Alex,
 
Boot into that and use it to delete the entire HD. Delete from the right most partition. After leaving it unallocated, right click > new and format into ext3. Once succesfull, Quit application and eject CD.

 

 
I'm looking at the GParted window but I'm not sure how to do this.
 
I've right-clicked at the unassigned portion of the disk (/dev/sda1) (290Gb) and clicked on Delete, now it appears as a pending task in the bottom of the window.
 
But the Delete option is not available for /dev/sda2 (the 7.2Gb partition where Ubuntu is installed), how do I delete it?
 
a) If I right-click on it the only option available is Resize/Move, which allows me to increase its size but not delete it.
 
b) There's another option on the menu Device>Create Partition Table, the default option is msdos type, other options are: aix, amiga, msd, dvh, gpt, mac pc98, sun, loop. Is this how I should erase the HD? is the msdos type the correct one?
 
Thanks!!!
 
Alex.

---

### Post by AE000 on 2009-06-02
> **raymondhenson said:**
> 
Boot into that and use it to delete the entire HD.  Delete from the right most partition.  After leaving it unallocated, right click > new and format into ext3.  Once succesfull,  Quit application and eject CD.

I finally found the way to erase all the partitions and created a new Ext3 one.

> **gordintoronto said:**
> A small suggestion: allocate a small partition (such as 30 GB) as "root", then the swap partition (twice as big as your memory) and the rest as "home".  This could make things easier when it's time to upgrade versions.

Should I add these two inside the primary Ext3 partition? or adjacent to it?

Should both of them be Ext3? Will it be until I install Ubuntu that I'll tell it which will be "swap", which "home" and which will be "root"? (because on Gparted I can't rename them as such).

Thanks in advance,

Alex.

---

### Post by raymondh on 2009-06-02
Hello Alex,

I'm trying to follow the thread and/but decided to post a small guide..... as if I were doing this myself on my blank HD, using gparted to set/define partitions first,  with an intention to just 1-boot ubuntu.  You may have accomplished some steps already.

Using GParted
- Click on the unallocated space > partition > new > choose extended for the whole space > click apply
- Click on the newly created extended partition.  Intention is to make 3 partitions
1.  Make a Swap partition, about 1-2GBs, and format it as SWAP
2. Make a / (ubuntu root) partition, about 20 GBs and format as EXT3
3. Make a  /home partition, allocate the remaining space, and format as EXT3
- Click apply.  Once done, quit gparted and boot into the liveCD

In the LiveCD, and when you get to the partitioning stage (installer)

- Choose MANUAL
- Select the SWAP partition and edit.  Choose USE and select SWAP (for the type)
- Select the ROOT partition and edit.  Choose USE, Ext3 and select type  /
- Select the Home partition and edit.  Choose USE, Ext3 and select /HOME

From hereon, continue with the install.

I hope this helps you.  Again, you may have done some steps already and if so, I apologize if I made this sound silly/trivial.  No offence meant :)

Let us know how goes.

---

### Post by AE000 on 2009-06-02
No offense taken at all, this guide is exactly what I needed, and it worked almost perfectly:

I installed Ubuntu 9.04 instead of 8.10 and during the installation I got messages for several files that did not match the ones in the CD and I chose to skip them to avoid aborting the process, these are the files:

/target/usr/lib/dri/r300_dri.so
/target/usr/lib/mono/gac/System.Drawing/2.0.0.0_b03f5f7f11d50a3a/System.Drawing.dll
/target/usr/lib/oppenoffice/basis3.0/program/libdbtoolsli.so
/target/var/lib/dpkg/info/evolution-common.md5sums

After the installation completed I found all of these files in my root folder (each in their destination) so does this means I'm ok to go or should I do something about it?

Thanks!

Alex.

---

### Post by raymondh on 2009-06-02
> **AE000 said:**
> No offense taken at all, this guide is exactly what I needed, and it worked almost perfectly:

I installed Ubuntu 9.04 instead of 8.10 and during the installation I got messages for several files that did not match the ones in the CD and I chose to skip them to avoid aborting the process, these are the files:

/target/usr/lib/dri/r300_dri.so
/target/usr/lib/mono/gac/System.Drawing/2.0.0.0_b03f5f7f11d50a3a/System.Drawing.dll
/target/usr/lib/oppenoffice/basis3.0/program/libdbtoolsli.so
/target/var/lib/dpkg/info/evolution-common.md5sums

After the installation completed I found all of these files in my root folder (each in their destination) so does this means I'm ok to go or should I do something about it?

Thanks!

Alex.

Hello Alex,

First off, am glad you have ubuntu working :)  Enjoy your learnings and your new system.  Before we get to those files, is everything working fine?  Wireless? Sound? Browsing? Shutdown/suspend/hibernate?  Desktop effects?  How about trying to play videos or accessing sites that require flash?  How about making a test document then saving then re-editing same document?  Terminal working fine?  Are you able to update and upgrade with no problems?

If all of those work, and so much more ... then you're good to go.  Time for you to enjoy your hard work.  And should you receive an error because of those files, let the forum know and we'll go from there.

En ahorra buena y que tengas un bien ubuntu-ing :)

Regards,

---

### Post by AE000 on 2009-06-03
Thanks Raymond, so far everything has worked very good.
 
I wanted to ask you one last thing: if I install my old HD (with windows XP) as a slave, should I be able to see it from Ubuntu to copy files or access the music on it?
 
Thanks!
Alex.

---

### Post by raymondh on 2009-06-03
> **AE000 said:**
> Thanks Raymond, so far everything has worked very good.
 
I wanted to ask you one last thing: if I install my old HD (with windows XP) as a slave, should I be able to see it from Ubuntu to copy files or access the music on it?
 
Thanks!
Alex.

Hi Alex,

You will have to mount it.  And yes, ubuntu/linux can read NTSF (that is the format, right?).  

This link may help you.  Sorry, If I was at home, I could send you better links as I have bookmarked quite a few (and used a couple of them for reference).  Alas, I am on the road and my brain memory and google-fu aren't working quite well now :)

try this link.

[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)


Post back in a new thread how goes mounting and we can go from there whether, success or errors.  Till then, have fun tweaking your new ubuntu install.

PS, as this thread involves partitioning, would you like to mark it solved?  Go to your first post > edit > advanced > type SOLVED in front of your thread title > save.  It may help another member who experiences the same challenges you had ;)

Regards,

---

