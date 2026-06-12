---
title: "question on ext3 fs"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by DarkManX4lf on 2005-07-05
im thinking to make the final leap to linux and using windows as the secondary OS.  now i have 3 actual hard drives,

40gig (20gig ntfs, 20gig linux)
120gig ntfs
200gig ntfs

what i want to know is if i convert the 120 and 200gig drives to ext3 can i read/write to them in windows?

can i install windows progs to directories in the ext3 drives, from windows?

---

### Post by manicka on 2005-07-05
Windows won't read ext2/3 natively (how surprising) so you won't be able to install programs on those partitions. There's  couple of 3rd party programs that allow read/write access of ext2/3 partitions in windows. There's one I use but it's been that long since I booted into windows I can't remember it's name. (it's a bit clunky but does the job when necessary)

If you really want to share data between systems why not try formatting with fat32 on one of them, which linux reads and writes to without problems.

---

### Post by DarkManX4lf on 2005-07-06
well from what i read fat32 files can only go up to 4GB in size....this program you speak of that will let me read/write to ext3, is there anyway to use that program and use it to install programs to that ext3 partition ?

---

### Post by manicka on 2005-07-06
DarkManX4lf,

Okay, I booted into windows (ooh... I feel so cheap, you owe me one) to find out it's name. The program is caleld LTOOLS and you can get it [here](http://www.it.fht-esslingen.de/~zimmerma/software/ltools.html) . 

It will give you read write access to ext2/3 but you won't be able to install any programs on it as it is just a program that sits on top of the windows OS rather than integrating with the system.

It's probably not what you're looking for but it's a start. I don't think what you're after exists. Maybe someone else might know.

---

### Post by DarkManX4lf on 2005-07-06
thanks i will give that program a try, sorry to make you boot up into windows :)  hopefully someone knows if i can mount ext3 as a drive in windowsxp

---

### Post by manicka on 2005-07-06
[QUOTE=DarkManX4lf] sorry to make you boot up into windows :)[/QUOTE]

That's okay. Always nice to be reminded why I spend most of my time in Linux. 

Now if I could just convince my partner and children to do the same, then I could kiss my dual boot goodbye forever.

---

### Post by DarkManX4lf on 2005-07-06
[QUOTE=manicka]That's okay. Always nice to be reminded why I spend most of my time in Linux. 

Now if I could just convince my partner and children to do the same, then I could kiss my dual boot goodbye forever.[/QUOTE]


i would kiss my dual boot goodbye too, its the games that are holding me back  ](*,) 


also one more thing, is it true that fat32 can only support a unique filesize of 4gigs and no more? so like a 4.5gig file (dvd iso or something) would not work ?

---

### Post by manicka on 2005-07-06
[QUOTE=DarkManX4lf]

also one more thing, is it true that fat32 can only support a unique filesize of 4gigs and no more? so like a 4.5gig file (dvd iso or something) would not work ?[/QUOTE]
 That may be true. Whenever I used to back up a dvd using dvd shrink to a ntfs partition it would just be one iso file, but when I backed up to a fat32 partition it would split the file  into 1gb segments that dvd decrypter would put back together when burning.(Thanks to MrBass I now use these programs successfully in Linux instead and don't have these issues).

I always wondered why this happened. Perhaps the 4gb limit for fat32 is the answer

---

### Post by DarkManX4lf on 2005-07-06
so another question popped into my mind about the fat32 file system... so here's the setup:

i download alot from bittorrent, dvd images :), and among other things, and usually thse dvd images are broken up into 40meg or so parts, but *sometimes* these dvd images are whole dvd images and are exceeding 4gigs.

and the question:

So if i happen to download these dvd images which are over 4gigs from any download client (bittorrent, limewire etc) what would happen ?

---

### Post by DarkManX4lf on 2005-07-06
Up !!

---

### Post by manicka on 2005-07-06
okay, I just tried to copy a 4.3gb iso onto one of my fat partitions and it failed at the 4gb mark

---

### Post by DarkManX4lf on 2005-07-06
damn thats bad news

---

### Post by DarkManX4lf on 2005-07-07
also if i have more than one ext3 partition, how would it show up in the filebrowser ? what would be the second partition be named? filesystem2 ?

and how do i format a drive to ext and mount it?

---

### Post by manicka on 2005-07-07
[QUOTE=DarkManX4lf]

and how do i format a drive to ext and mount it?[/QUOTE]

Is the drive already formatted in ntfs or whatever and mounted in linux. Which drive is it? hda,hdb or c?

you might find this howto useful

[http://www.tldp.org/HOWTO/Partition/partition-5.html](http://www.tldp.org/HOWTO/Partition/partition-5.html)

---

### Post by DarkManX4lf on 2005-07-07
[QUOTE=manicka]Is the drive already formatted in ntfs or whatever and mounted in linux. Which drive is it? hda,hdb or c?

you might find this howto useful

[http://www.tldp.org/HOWTO/Partition/partition-5.html](http://www.tldp.org/HOWTO/Partition/partition-5.html)[/QUOTE]

yea the drive is ntfs and its hdb, if i format this hdb do i have to create a swap partition for it ? or can i just make the whole thing ext3?

---

