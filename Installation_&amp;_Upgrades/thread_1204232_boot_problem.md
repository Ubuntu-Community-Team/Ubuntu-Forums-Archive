---
title: "boot problem"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by Aaron.A on 2009-07-04
hello
i'll try to explain the problem as plainly as possible. i have vista 32 and a wubi install of jaunty. i was ready to upgrade to a partitioned ubuntu install.
so, i followed a tutorial, and used "Parted Magic" to resize my windows partition. that took over 7 hours. afterwords ubuntu won't boot!! windows also didn't boot at first but fortunately it was able to fix itself using vista's repair tool. 

so, here's where i'm at now: vista is running, wubi will not boot after using parted magic to resize my partition. the only clues it gives me is windows failed to boot, check files!
and it tells me wubildr.mrb is the problem.

anyone familiar with this problem? 
thanks in advance =)

---

### Post by merlinus on 2009-07-04
You need to use vista's disk management tool to resize its partition.  There are numerous posts on the forum about those who did not, and suffered dire consequences.

Also important is to first disable the paging file, reboot, delete pagefile.sys (or some similar name), and defrag several times.

Then you can resize and do a side-by-side installation of linux from the live cd.

---

### Post by presence1960 on 2009-07-04
good points merlin, also uninstall wubi from Control Panel in Vista as you would any other program.

When finished with those suggestions Boot from the Live CD and install Ubuntu. For future reference it is safer to resize Vista with it's own disk management tool even though some have had success with gparted and such. But as Merlin mentioned quite a few have had less than desirable results doing it that way. Also Ubuntu Live CD has gparted on it or for an even better option download the iso for gparted Live and burn the image to a cd or a USB media if you can boot from USB. Get gparted Live Cd here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by raymondh on 2009-07-04
and if you are curious about gparted and NTFS and its' difficulties .... here's a good read from the gparted forum, tutorial posted by CMDR.

[http://gparted-forum.surf4.info/viewtopic.php?id=2892](http://gparted-forum.surf4.info/viewtopic.php?id=2892)

post 1.

Another reason, adding to merlin's suggestion to use the Vista tool to work on a Vista partition.

---

### Post by Aaron.A on 2009-07-04
thanks for the help everyone!
the biggest thing for me was not losing my data because i've done a lot already. 
the tutorial i saw never mentioned using a vista partitioner so i used the one they
talked about in the tutorial. fortunately i found a fix and everything is back how it 
+ i have my newly freed space. 

what i did was backup my disc folder from the ubuntu install. 
then i un-installed. i then reinstalled and rebooted allowing 
ubuntu to do its 'first boot' setup. 
then i booted back into vista, replaced the disc folder in my new
install with the one i backed up, then booted back into ubuntu ftw!

=)

---

### Post by Aaron.A on 2009-07-04
ok i really broke it now. 
i used LVPM to move my wubi installation over to my the space i created with parted magic and rebooted. i tried the ubuntu boot options(5 different options including a mem test and "recovery" modes)and everyone of them did nothing but pop up a black screen with one line of text. saying something like boot from this or that...

so i decided to restore my partition using the vista disk man tool. 
i never actually officially "uninstalled" ubuntu i just reclaimed the 
space i installed it to with vista disk man. then fixed the boot options. 

so now i've reinstalled wubi and when i try to boot i get
```
try (hd0, 0): ext2
```can anyone recommend, ummm, something? 
i have a vista disc. i don't have a restore point.
i'm on a brand new vaio and i'd really rather not
lose my whole harddrive. especially my wubi 
"disk" cause i've got it setup just the way i want it

---

### Post by earthpigg on 2009-07-04
off topic, but i think wubi needs to have _*a lot*_ more warnings about its limitations _*prior*_ to install.

---

### Post by Aaron.A on 2009-07-04
=) 
well, as a new user i really can't comment...
i like the fact that with wubi i can access my windows files. i can download the same
torrent with either operating system this way. so whether i'm working with ubuntu, or playing with vista my torrent continues downloading.

back on topic though, i'm de-fragmenting and cleaning up my hard-drive the best i can
to eliminate any errors that may be present. then i'm going to un-install wubi, defragment again, and re-install wubi to see what happens. but if anyone has suggestions please help!

---

### Post by presence1960 on 2009-07-05
wubi is meant to be a test drive to see if you like Ubuntu without having to partition your hard disk. I realize some use it forever though. I only installed it recently to gain knowledge about it . I played around with it for about 2 or 3 weeks then removed it. If you liked Ubuntu then go with a dedicated partition not wubi. You can access windows partitions this way also- as I see you mentioned that is a reason why you liked wubi.

---

### Post by raymondh on 2009-07-05
> **Aaron.A said:**
> =) 
well, as a new user i really can't comment...
i like the fact that with wubi i can access my windows files. i can download the same
torrent with either operating system this way. so whether i'm working with ubuntu, or playing with vista my torrent continues downloading.

back on topic though, i'm de-fragmenting and cleaning up my hard-drive the best i can
to eliminate any errors that may be present. then i'm going to un-install wubi, defragment again, and re-install wubi to see what happens. but if anyone has suggestions please help!


Hello Aaron,

You may want to google or check the sub-forums for compatibility with the Sony VAIO.  

Good luck.

---

### Post by presence1960 on 2009-07-05
wubi is meant to be a test drive to see if you like Ubuntu without having to partition your hard disk. I realize some use it forever though. I only installed it recently to gain knowledge about it . I played around with it for about 2 or 3 weeks then removed it. If you liked Ubuntu then go with a dedicated partition not wubi. You can access windows partitions this way also- as I see you mentioned that is a reason why you liked wubi.

With wubi you are kind of locked into the space you set for wubi. With a full install you can shrink & grow partitions, delete and create partitions provided you have the room to do so. You have a lot more flexibility with a full install. if your wubi gets full you are basically stuck, but with a full install you can shrink an adjacent partition and grow the ubuntu partition.

This is just my preference but I would go with a full install. If partitioning is something you are shaky on, we can provide some links to read to get you educated and up to speed on partitioning.

P.S. OOps! what happened here!! wanted to edit & wound up as a new post...lol

---

### Post by Aaron.A on 2009-07-05
> **raymondhenson said:**
> Hello Aaron,
You may want to google or check the sub-forums for compatibility with the Sony VAIO.  
 
good plan. i looked around and compatibility is good. i'm worried that the partitioning i did with parted magic, and the install i made with lvpm may have left a little shrapnel on my disk. may be buggy...
> **presence1960 said:**
> 
If partitioning is something you are shaky on, we can provide some links to read to get you educated and up to speed on partitioning.

it is definitely something i've had little to no experience with. i've got a pretty good understanding, but any advice is welcome. considering my vista partition actually survived parted magic i'm worried, like i mentioned above, that there are bugs i'm not seeing. i mean, for example, i was just playing ut while o&o defrags my system, and that damn blue screen assaulted me =o

Sony has built in factory recovery(love sony =)so i can wipe it all and do it right if it comes down to that. but i like to solve problems when i can =D

---

### Post by presence1960 on 2009-07-05
Unfortunately Vista has been known to freak out if shrunk by an outside utility. That's why even though it is possible a lot of us recommend using Vista's disk management utilty to shrink Vista to create free space for more partitions. Once this is accomplished we then use the Ubuntu live CD or gparted Live CD to create partitions.

Here is a good guide on partitioning:[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")
For a pdf Ubuntu Pocket Guide: [http://www.ubuntupocketguide.com/index_main.html]("http://www.ubuntupocketguide.com/index_main.html")

---

### Post by raymondh on 2009-07-05
Some more references if you plan to dual-boot 

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)  (thanks Herman)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)


As part of your preparation for dual-booting, you will have to plan ahead to minimize risks.

1.  Are your valuable files backed-up?  There will be no guarantees.
2.  How much space would you like to allocate to Ubuntu hence how much will you shrink Vista?
3.  Have you tested the liveCD for defects, MD5hash, and how the Ubuntu version relates to your system specs' & hardware (wifi, keyboard, sound, etc)?
4.  Do you plan to have a separate /home partition in Ubuntu *(which is where your files, seetings and tweaks will reside ... hence if you ever need to re-install or do a version upgrade, your /home can remain intact)* ?
5.  If you plan to separate /home, do you want to create the partitions prior to installing or, install and then create the separate /home?

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

6.  Do you plan to suspend/hibernate a lot?  IMHO, SWAP is ok at 1.5GB.

I am assuming that you have the Sony RECOVERY DISC's for Vista.  Here are sites that will be good to bookmark, just in case.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

And lastly, a link to help you reference while working with the Vista Disk management tool.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

I apologize for all the links (as they seem too much).  You'll agree that the more you read and prepare, the better chance for a successful outcome ;)

Good luck ... do post back if you need assistance.

---

### Post by Aaron.A on 2009-07-05
> **raymondhenson said:**
> 
I apologize for all the links (as they seem too much).  You'll agree that the more you read and prepare, the better chance for a successful outcome ;)

not at all overwhelming lol thanks!
mission success! i haven't tested booting back into vista yet because i just now booted into ubuntu and had to come on here with an update =) i found the partitioner 'advanced mode' on the jaunty live disc to be almost dummy proof. but i have read a lot and knew pretty well what i was supposed to be doing. i was able to completely scrub the failed dual install attempt i made using lvpm. i think i know what i didn't do ;) so, i used 1.5gb for swap, and used the 30 so gb i opened up with vista disk man for root

i would still like to get my settings back from my wubi install. i kept the entire "ubuntu" folder from my wubi installation so i know the information is there. if someone could point me in the right direction so i can get there quicker i'd be much obliged

---

### Post by earthpigg on 2009-07-05
ive never used wubi -- if you navigate to the ubuntu folder from wubi, can you peek at what is inside of it?

if so, try to find find /home/(username)/ and select 'view hidden files and folders'. all those things with .programname are the settings for that program.

copy them over the existing /home/(username)/.programname on your new ubuntu install, and it will restore the settings.

---

### Post by Aaron.A on 2009-07-05
> **earthpigg said:**
> ive never used wubi -- if you navigate to the ubuntu folder from wubi, can you peek at what is inside of it?

if so, try to find find /home/(username)/ and select 'view hidden files and folders'. all those things with .programname are the settings for that program.

copy them over the existing /home/(username)/.programname on your new ubuntu install, and it will restore the settings.

unfortunately all i see is a 17gb "disk" file ... 
but, i did just find a script that will allow me to view the contents, i believe. 
i'm going to have to modify it probably to read the location of my wubi "disk" 
but, what you just said + that i should be able to restore it, hopefully =) 

thanks!

---

