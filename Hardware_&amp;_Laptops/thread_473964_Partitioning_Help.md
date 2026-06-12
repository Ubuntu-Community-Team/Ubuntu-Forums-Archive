---
title: "Partitioning Help"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by Syndacate on 2007-06-14
I realize this is a popular topic and probably has been covered multiple times, but I cannot seem to find anything with my problem (nor the answer).

I have 2 HD's on my HP Pavillion 9000z, dual 80's.

I have 31.X Gb left on my D:\ drive and I want to make that a partition for kubuntu, the C:\ drive is full.

[img]http://i82.photobucket.com/albums/j271/Syndacate/Computer%20Stuff/WindowsPartition.jpg[/img]

Now I do realize that this isn't Windows help - but I'm not asking it, as you can say 31.X Gb is free on my D:\ drive (ignore the other 2 400's, they're external media USB drives).  Is there anyway I can allocate that 31.X Gb of unused data into a partition and install kubuntu on it?

I went to install kubuntu and ran into this when it asked where to install it:

[img]http://i82.photobucket.com/albums/j271/Syndacate/Computer%20Stuff/kubuntupartition.jpg[/img]

So I just wanna know if anybody knows how I can go about doing this so I can use that extra 30 gigs on my D:\ drive for kubuntu **_WITHOUT_** formatting the drive.

Then when I hit "manual" and go to how many Mb to allocate (as the window shows) it only lets me type 2000 - not 20000...anybody know why this is?  It starts off as "all" at the default of 80000 but I can't change it to 20000 or 25000 - it's only allowing 4 digits.

When I installed it on my desktop I had a fresh HD (due to a recent melt-down) so I was able just to partition the first 40gb off of that and it was peachy, but now windows has the primary partition and I'm not sure what to do.  I was thinking of finding a copy of partition magic and using that - but I haven't had much good exp with that.  Also, what do I format it as, exp3 or exp2.

Thanks in advance!

---

### Post by Gremlinzzz on 2007-06-14
Did ya try deleteing a partiton and making it free space.Then when installing choose use largest continuos free space.works for me and its the easies way to set up a dual boot.ubuntu does all the work.

---

### Post by brettr on 2007-06-14
The problem is your D drive is alreadty formatted in a NTFS format, so you can not install linux on that one straight away. First you must resize the D drive in order to be able to format the free space into a linux format ext3 is probably your safest bet. Now if i recall you should be able to resize the partitions from inside the installer. I have never installed kubuntu, but in the ubuntu install i am pretty sure that once apon a time i resized from the installer.

---

### Post by Syndacate on 2007-06-14
> **Gremlinzzz said:**
> Did ya try deleteing a partiton and making it free space.Then when installing choose use largest continuos free space.works for me and its the easies way to set up a dual boot.ubuntu does all the work.

When I click "use largest continuous free space" it tells me there's not enough space for any of the automatic things.

If I try to delete the partition it will delete all the data on that drive :(

---

### Post by logos34 on 2007-06-14
Did you try scrolling the the size up using the arrows to the right of the box? 

"Use largest continuous free space' won't work because there's no unallocated space on the drive--it's one big primary ntfs partition.

I'd try the Gparted live CD.  Resize/shrink the windows partition, create an ext3 root and swap partition on the rest (/dev/sdb2 mounting on '/', and dev/sdb3 1GB swap on /swap). Then run the Kubuntu install cd again.

edit:
here's the link
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Gremlinzzz on 2007-06-14
Delete hp recover and that 1gb partiton that will be enough room for kubuntu:D that would make 12gbs more than enough.

---

### Post by Syndacate on 2007-06-15
> **Gremlinzzz said:**
> Delete hp recover and that 1gb partiton that will be enough room for kubuntu:D that would make 12gbs more than enough.

Haha, I don't even know how to use that recovery partition - it came with the comp :-P

Anyways, I got the partition to work.  I used partition magic 8 (so sue me) but didn't format it (just allocated it as a partition, unformatted, leaving the formatting for kubuntu) but then I came across this error:

[img]http://i82.photobucket.com/albums/j271/Syndacate/Computer%20Stuff/error-1.jpg[/img]

I'd probably research the problem more but I don't even get what the heck the problem is :(

I was creating 25000 (mb) as ext3 (tried it on primary and the other setting) setting it as "/" for mount location (that is "root" - right?), and a 2gb partition set as swap, and it gives me that, blah...

Blah, everything went flawlessly when I installed it on my desktop but I'm having nothing but probs here :(

---

### Post by logos34 on 2007-06-15
I've heard it said in these forums that Parttion Magic does not work well with linux.  If I were you I'd get the Gparted live cd and use that to carve out two primary partitions for root and swap.  Then go through the install again and set the mount points in the prepared partitons...it may force you to reformat them.  

Not sure what else the problem could be.

---

### Post by Syndacate on 2007-06-15
> **logos34 said:**
> I've heard it said in these forums that Parttion Magic does not work well with linux.  If I were you I'd get the Gparted live cd and use that to carve out two primary partitions for root and swap.  Then go through the install again and set the mount points in the prepared partitons...it may force you to reformat them.  

Not sure what else the problem could be.

Yeah, I usually refuse to reduce myself to partition magic but I had no idea what else to use.

Though it really shouldn't matter, it's not like I used partition magic to format the space.  I just used it to separate the used space into its own partition.  So windows recognizes the ~30gb as unallocated, unformatted disk space.

So it shouldn't matter as that partition can be formatted w/ kubuntu during its installation.  I tried a 25gb ext3 and a 2gb swap - but I get that weird error msg :(

---

### Post by Syndacate on 2007-06-15
*bump

I know one of you guys knows - I just don't even know what it's trying to tell me so I can research the problem more :(.  Though something tells me it's a relatively common problem, I obviously don't have enough of something...which is weird b/c 25gb ext3, 2gb swap partition, 2gb ram and a processor that's not even a year old - it should DEFINITELY be able to run kubuntu, the requirements aren't that low :crook:.

---

### Post by Syndacate on 2007-06-17
Eh...plz?

Nobody seems to know anything about this...

---

