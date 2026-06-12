---
title: "Formatting a drive via Ubuntu"
date: 2008-10-23
forum: General Help
---

### Post by oglach on 2008-10-23
Ok,

I had windows vista on my laptop.
It was formatted and i tried overrite it with 'tiny xp beast edition' which now asks for windows pro service pack 2' when i start up.

Ive tried overrite it with vista.
Anyway, to cut a long story short. I used linux lived cd (SLAX) and also ubuntu. I just need to know how to format the drive i have windows on, its about 60gb, but i want to format it so i can isntal xp on it.
And im also goin to want to be able to install ubuntu on 2nd partition but gota sort this 1st.

Any1 have any help at all please, last resort.

---

### Post by jerome1232 on 2008-10-23
Do you have a Windows xp install disc? You should be able to just boot up with it and do the formating from there.

---

### Post by oglach on 2008-10-23
> **jerome1232 said:**
> Do you have a Windows xp install disc? You should be able to just boot up with it and do the formating from there.

I have original windows vista disc! And i even downloaded to xp pro discs to try overun it when it asks for xp pro.

Will not work, i have ubuntu running through cd, was wondering how to format my c:/ drive?

---

### Post by jerome1232 on 2008-10-23
System-Administration-Partition Editor, that will pull up gparted you should see all your partition there you can format to your will. Although I really think something else is up, Vista should  be able to see the hard drive regardless of file system.

---

### Post by oglach on 2008-10-23
ok i went there and have this :

Partition`/  Filesytem/Mountpoint/Size/   Used/   Unused/  Flags
/dev/sda1     fat16                109mb  7mb     102mb     
unallocated   unalcoated            10gb         ---       ---
/dev/sda2      ntfs     /media/OS    64gb 5gb      59gb    boot


So theres 3 partitions

1. Havnt clue what its for.

2. Unallocated is 10gb, would it be possible install ubuntu on that from the start of instead of having it on a disc

3. Is which i want to format and then run XP over it

also beside NTFS on 3rd patition is a pic of keys

---

### Post by jerome1232 on 2008-10-23
> **oglach said:**
> 
also beside NTFS on 3rd patition is a pic of keys

1: that's a fat16 partition, an odd file system indeed, very small too, Can you mount it and see what's in it? Should be in your Places menu.

2: Yes you could install Ubuntu and it will fit nicely in a 10GB space, you will need to create a swap partition too, ~512 MB is usualy enough.

3: That's your ntfs partition, you have vista on there currently? And you want to format it and put xp on there? It has a set of keys because it's mounted currently.

In case you didn't know already formating a partition delete's EVERYTHING on it, so if you have pictures and etc on there you are going to want to back them up.

But really you can do this all from the XP installer, what kind of errors was it giving, why wouldn't it work?

---

### Post by oglach on 2008-10-23
1. All thats in 'places' is homefolder,desktop, documents, music, pictures,videos, computer, cd/dvd creator, os, network, conect to server, search for files.
When right click it wud let me format to whatever, no 'mount'



2. Ok im going to do that once i see how to create a swap partition. Im currently running ubuntu from cd, but id like to have it installed.


3. This had vista, i then tried instal 'tiny xp, beast edition' since then when i start up all i get is please insert xp pro serrvice pack2 disc' and even restartin and booting with original vista disc wont let me over rite it.


Oh and i have saved files to a pc a thome, so i can delete anything! In fact, if i could wipe everythign and have xp ruunin from 1 partition and ubuntu on another it would be perfect.

---

### Post by jerome1232 on 2008-10-23
If you want to try restoring vista:

I Haven't used a vista disc yet, but there should be a way to drop to a recovery console, I would try that and type these commands in to restore your vista. I'm not sure how to actually get the recovery console (in xp you have to hit the letter 'r' at a certain point I think)

```
fixboot
fixmbr
```

Otherwise I would just use xp to nuke everything and start from scratch.

---

### Post by bodhi.zazen on 2008-10-23
Take care that you understand how Linux uses and names partitions or you will over write or lose data ;)

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

You can install Ubuntu into the unallocated space. Ubuntu needs 2 partitions, one for / (root) and one for swap. You can do without swap if you have enough RAM (1.5-2 gb).

See also : [uhelp]community/Installation[/uhelp]

---

### Post by oglach on 2008-10-23
It wont let me nuke over everything, thats the problem, im goin to have to format it and then instal, because no matter what i do it asks for xp pro service pack 2 disc,

u see i tried instal a modded version of xp (tiny xp beast editon) 

so thats why want to format it through ubuntu? then reinsatll trhough an original disc?

---

### Post by oglach on 2008-10-23
> **bodhi.zazen said:**
> Take care that you understand how Linux uses and names partitions or you will over write or lose data ;)

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

You can install Ubuntu into the unallocated space. Ubuntu needs 2 partitions, one for / (root) and one for swap. You can do without swap if you have enough RAM (1.5-2 gb).

See also : [uhelp]community/Installation[/uhelp]

I typed free in terminal :
     TOTAL......USED....FREE.....SHARED....BUFFERS.....CACHED
Mem: 983736.....853472...50264.....0........102812.....531052
-/+BUFR/CAHCE   219608...684128
swap: 0......0.....0



Do i have to create a swap? or will it be ok?
Ther shpould be nothing on my laptop, any files, so i dont mind about losing anything :)
Nice one for link, going read up on it now, id say il have to do swap

---

### Post by bodhi.zazen on 2008-10-23
Looks like you do not "need" a swap, but it may be a good idea.

---

### Post by oglach on 2008-10-23
I decided give up. Tried install ubuntu on unallocated space and had way 2many options when it showed me the partitions!dno what primary and other 1 means, or fat16, swap , loads stuff!  

Is their no simpel way of just formatting the other partition! HEADs fried!!!!!

---

### Post by oglach on 2008-10-23
3 partitions!
1. is dev/sda/fat16 dont know what that is, so i want toget rid of it, just tell me how!

2. unallocaterd, im goin to try instal ubuntu there once i format main part and install xp!

3. Im going to format this which the 0S is,so  what do i format them too?

ext2? ext3? fat32? fat16? xfs? ntfs? what

Im going to use xp on it once it formats

what do i format it thto o?, have about 10options, i dnt know what they mean.



once i format that and install xp i plan to use unalocated space for ubuntu! trying to sort it, any help appreciated! :(

---

### Post by jerome1232 on 2008-10-23
You gotta make sure everything is unmounted, if it has that key icon just right click and then click umount. You can then delete partitions the partitions.

Delete every partition in site. Then use the Windows xp cd to create partitions for itself, matter of fact you can use the xp cd to nuke/install anyways you don't need to do this in gparted from the ubuntu live cd.

---

### Post by oglach on 2008-10-23
ok i deleted all partitions and ran xp disc, its been formatting at 0% the last 30mins!


something wrong there anyway!!!!


Doubt its goin to work?

Ok, to install ubuntu, i stick in disc, select INSTALL ON PC! now i get option of partitions, do i create 2?

2 primary, or 1 primary and 1 other

---

