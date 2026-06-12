---
title: "ubuntu/vista dual boot stuff--please help"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by Mirages on 2009-06-15
hey,
I want to dual boot ubuntu/vista. I have never run a dual boot before. I am new to linux and ubuntu. I was using the wubi for a while. I did some research but I have hit that point where its a little overwhelming and I need to be the one asking the questions. I found a few guides, one of which has been quite helpful with lots of info but doesn't quite meet my needs. [HTML]http://members.iinet.net/~herman546/index.html[/HTML]

1)can I delete the DellUtility partiton? freeing up space for another primary partition (like the swap?)

2) at the moment I cant make swap a primary partition cause if ubuntu is going to be a primary then I have used up all 4 spots.
  A)(partition newb question)if I made ubuntu an extended partition and placed the swap as a logical within that extended partition would ubuntu still dual boot properly alongside vista even though it is no longer a primary partition? 
  B) my computer has 2gb of memory built in. so is the swap all that necessary? I don't intend on using ubuntu for gaming except for maybe light games like World of Goo and Fallout1/2/Tactics. so maybe the swap isn't required?
  C)Swap as a file: eliminates the need for the partition. I found a thread on it but I dont think I am capable of making it work... [HTML]http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile[/HTML]

3)What format should I install ubuntu as? ext3 ext4 or ntfs?
I ask because my vista partition is ntfs. I use a external hdd in fat32 so it is compatible with both. I would like to reformat the external to something that will still be compatible between the 2 operating systems. Is ntfs compatible with ext3/ext4? what are the possiblities because I don't know.

I am using a dell latitude d630 laptop with a 120gb hdd and 2gb of memory it already has 3 out of the possible 4 primary partitions.

-partition 1: DellUtility its a small 62MiB partition  and it only uses 7MiB of that according to Gparted. 
     ^^is this partition really that important for my laptop to function? is it like an extension of the BIOS? could I remove it?

-partition 2 and 3: recovery and vista: from what I know these 2 partitions are always installed on the same sector of the hdd and not supposed to be moved. so if I deleted partiton 1 (assuming I can delete it) I wouldn't be able to slide the 2 vista partitions to the beginning without possibly screwing something up.

currently the 3rd partition is just over a 100gb. 35gb of it is being used by vista. I use vista mostly for gaming and want to leave space for the addition of a few more games. 

4)how much space should I leave at the end of the vista partition when I resize for the addition of new applications. at this point I had already freed up as much space as I felt I could in the partition by removing all the crap applications I don't use. I still kept the MS stuff like office 2007 (for its great templates) and outlook/IE because aren't those 2 apps integrated into vista? and vista will not work properly if I remove IE and Outlook? I guess that could be a 5th question.

5)can I remove MS IE and outlook? I dont want to get rid of MS office yet, even though Openoffice almost replaces it... except for the templates.

any help is appreciated!

---

### Post by merlinus on 2009-06-15
Here are a few suggestions:

Do not remove your restore partition -- you may need it someday.

Use vista's disk management tool to resize its partition, and be sure to delete temp and other unneeded files and defrag beforehand.

I woul definitely create an extended partition for ubuntu root (/) and swap.  Swap can be 1.5G, and I would place it at the very end of the hdd.  You may also want to create a separate /home partition, as it will make upgrading to new versions and/or reinstalling much easier.

Use ext3 -- ext4 shows lots of promise, but given the threads detailing problems, best to stay with the tried-and-true.

Ubuntu will be able to read and write to your ntfs partition, so you can use that for storing data.

As for space, 10G for / and another 10G for /home.  You will need to leave empty space for vista for defragging purposes, as well as installing new apps.  I doubt that you can get rid of IE. but Open Office is as good as Word.

---

### Post by brncao on 2009-06-15
DellUtility: [http://www.goodells.net/dellutility/index.htm](http://www.goodells.net/dellutility/index.htm) This should answer your questions regarding it.
 
Since I have a Dell too here's my layout.
 
I have 2 hard disks in my laptop. The image is showing disk1 (sdb). I have Windows and Ubuntu on disk0 (sda), but we'll focus only on sdb.
 
DellUtility - Primary
Recovery - Primary
Windows Vista - Primary
 
MediaDirect - Logical inside Extended
Everything Linux - Logical (all that unallocated space in the middle would be for Linux after you've added Vista first). But please remember the images are just for demonstrative purpose.
 
Now assuming you have mediadirect, you'll need to extend the extended partition all the way to the left (notice the cyan border). From here you can start adding logical partition such as "/", "/home", "swap", etc. I had operation failures before when I tried to add logical partitions. Make sure you check "round to cylinders."

---

### Post by Mirages on 2009-06-15
thanks for your answers! I looked back on my post and its an absolute mess, hahaha. I am glad it got something across. 

thanks for the link about the dellutility. looks like I dont really need it. its not a recovery partition by itself, turns out you need another seperate Dell PC-Restore partition for that. I will hold onto it anyways.
 
I will create an extended partition and house all my linux stuff within it but.. stupid question, will the boot loader still work properly if all the linux stuff is not in a primary partition? or are primary and extended partitions one in the same just that extended has lots of smaller partitions within it?

I am not sure how to seperate the / from the /home into different logical partitons, I see what you mean when you say it makes upgrading to new releases easier.

I am pretty much set to partition the drive for ubuntu . cleaned up my filesystem, defragged it, and backed everything up

thanks for all your help answering my crucial questions now I think I know enough to make it work.

its time to learn by doing :)

---

### Post by Mirages on 2009-06-15
just another question...

GParted works well for resizing vista? cause its taking forever! and I defragged beforehand

just so you know exactly what I did...
I booted into Live CD
started up GParted
resized the partition from 109gb down to 55gb 
immediately afterwards I clicked apply
and its been running for quite awhile now....... its on the "real resize" process

---

### Post by merlinus on 2009-06-15
Use vista's disk management tool to resize its partition after defragging.  Otherwise, as you are discovering, you can't do much of anything.

It sounds like it's too late, however.  At this point, let gparted run until it is finished or throws up errors and quits.

---

### Post by Mirages on 2009-06-15
I wish I could do away with vista all together :/

I hate having to still use it for games.

I just dont have the patience or savviness to mess with WINE

EDIT: and by he way GParted worked :) it was alot to resize... so I guess not surprising it took awhile

---

### Post by Mirages on 2009-06-15
ok I am posting as I am going thru the process and I have figured out at which point I specify which partition is root and which is home.

so now my question is when I install a new application. I assume its installed in the /home partition not the / partition. the root or / partition is just the underlying framework and all changes I make like applications are made in my /home partition.

just want to clarify

---

### Post by merlinus on 2009-06-15
Glad it is working.  Programs are generally installed in the filesystem, but setup and configurations live in /home.  Most of them will give you a menu entry.

---

### Post by Mirages on 2009-06-15
the file system being / , correct? I suppose 10g will be enough to hold plenty.

then again I could just put it all on 1 partition instead of 2 separate.

---

### Post by merlinus on 2009-06-15
10G for / is plenty unless you will be installing loads of apps.  I am only using 3.6G of space, and have a bunch of programs installed.

---

### Post by Mirages on 2009-06-15
alright this worked out great. not bad for a first dual boot set-up. 

Merlinus, thank you so much for all your input, it means a lot.
I was really trying to get it right the first time and it looks like I have. 

this was a nice experience to have under my belt. I have learned much about linux and computer hdd partitioning

the next thing I have to learn is the bash shell linux terminal command line thingamajig :D

---

### Post by merlinus on 2009-06-15
Escellent news.  Good for you, and happy ubuntuing.

---

