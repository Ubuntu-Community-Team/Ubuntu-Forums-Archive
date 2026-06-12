---
title: "[SOLVED] Exact duplicate of entire HDD"
date: 2008-07-30
forum: Hardware
---

### Post by prshah on 2008-07-30
Hello,

I have a 20Gb notebook ide hard disk drive, that is having some partition corruption. Before I do anything to fix that, I'd like to make a perfect copy of the entire HDD. 

partimage does not create the images, fails with "unknown partition" error. When the drive is plugged in via USB enclosure, sudo fdisk shows 4 fat16 partitions, but attempting to mount any of them fails.

fat16 partitions from other hdds work fine. (imaging, mounting). There are no bad sectors in this hdd.

Is there anyway for me to make an exact copy (bit-by-bit copy? bit-level copy?) of this hdd? 

I hope to make an exact copy, then try some recovery stunts, so that if the stunts fail, I can restore the exact copy back, before trying something else.

I'm wondering if the "dd" command will do it; but I'm not experienced enough to use it correctly, and will appreciate any advice/pointers. Of course GUI programs/solutions will be more welcome.

---

### Post by c2olen on 2008-07-30
I just did this last week, when I had to buy a new notebook because the older one died on me.
As you have already mentioned, the 'dd' command will do just what you want.
Be carefull though, you need to know what disk is what, before you start.

Since you mentioned an IDE disk in your notebook, I can safely assume it will be /dev/hda.
Plug in another disk (probably USB), which will become /dev/sda. (be sure to check it using 'dmesg' or 'sudo fdisk -l' first!!).

Then simply do '#> dd if=/dev/hda of=/dev/sda' and sit back and get a cup of coffee.
Replace hda and sda by your configuration.

I would also do this from either single user mode or a live CD session.

good luck

---

### Post by TenPlus1 on 2008-07-30
If you already have partition corruption then try to backup what files you can onto a completely different hard-drive and re-partition/format the failing one, possible to either Ext2/3 or Fat32/Vfat...

---

### Post by evets25 on 2008-07-30
There is also commercial software that does this sort of thing. For instance, there is Norton Ghost (which I've never used, but appears to be the most common) and Novell zenworks imaging (which is what I am familiar with), which is part of Novell's commercial zenworks suite. There may be other programs that do it, but they are probably expensive. using dd is probably your best bet if you don't have access to a copy of ghost.

---

### Post by hengvanna on 2008-07-30
I can't hear the sound from my laptop (Lenovo Y410) when I play music. I spend a lot of time to search the solution on the internet.

Could you please help me about this?

----------------------------------------


Vanna

---

### Post by evets25 on 2008-07-30
hengvana: Please start your own thread, that is a completely separate unrelated issue.. However, if you're talking about the y**5**10, not the y410, then take a look at [this]("http://ubuntuforums.org/showthread.php?t=870681") thread...

---

### Post by prshah on 2008-07-30
> **c2olen said:**
> 
Then simply do '#> dd if=/dev/hda of=/dev/sda' and sit back and get a cup of coffee.

Thanks, this is just what I was looking for. Very detailed, with pitfall warnings. Just a small question though; can I redirect the output to a file, rather than another device? in that case, I assume to command will become ```
dd if=/dev/hda of=~/hddbackup
``` or does it get more complex than that? Do I need to use any bs (blocksize) parameters?

> **evets25 said:**
> There is also commercial software that does this sort of thing. For instance, there is Norton Ghost 

Ghost is wonderful, I've used it often before. But now I have no access to Windows anymore; thanks for the suggestion, though.

---

### Post by evets25 on 2008-07-30
yes, dd can output to a file too. Well, technically speaking, in unix, "everything is a file" (including /dev/sda), so it always does an output to a file. In fact, the "of" stands for "output file." :) 

But no, seriosuly, dd can make a .iso file as an output. I forget the exact syntax for it; it's probably in the man page somewhere. ("man dd")

---

### Post by Wheel_nut on 2008-07-30
> **prshah said:**
> 
Ghost is wonderful, I've used it often before. But now I have no access to Windows anymore; thanks for the suggestion, though.

I use Seagate Disk Wizard which will image a Drive to another Disk or DVD(s) or CD(s) or even a USB Key. 

Now, You may have to use a Windoze machine to create a bootable CD before you can use it with Linux. I believe that the Bootable CD uses a Linux OS and then runs the Disk Wizard under Linux.

Now, I have to admit that I am not a Techie so I can't answer questions below the level of the User interface.

R

---

### Post by ByteJuggler on 2008-07-30
Just to add and to clarify what's already been said:

```
sudo dd if=/dev/hda of=/home/user/blah.img bs=16384
```

This will copy a bit perfect image of /dev/hda (being the first IDE hard disk) to a file in folder /home/user, called blah.img, using a block size of 16384 bytes.  Depending on the hard drive, certain multiples of 2 will help optimize the transfer time.  16KB (16384 bytes) is a reasonable generalization and relatively close to optimal for many drives.  One can then restore this image onto any other same size (or larger) hard disk if needed using eg

```
dd if=/home/user/blah.img of=/dev/hda bs=16384
```

for example.

HTH

---

### Post by breakthrow on 2008-07-31
Hi to all,

You should make backup image of your hard drive. Is this image option doesn't work for you the use stellar phoenix [linux recovery ]("http://www.data-recovery-linux.com")software which will recover your data after formatting the hard drive.

---

### Post by c2olen on 2008-07-31
> **prshah said:**
> Thanks, this is just what I was looking for. Very detailed, with pitfall warnings. Just a small question though; can I redirect the output to a file, rather than another device? in that case, I assume to command will become ```
dd if=/dev/hda of=~/hddbackup
``` or does it get more complex than that? Do I need to use any bs (blocksize) parameters?

If you are just cloning your harddisk to another disk, there is no need to put in your blocksize. Make sure your target harddisk is at least the same size as the originating disk!

I've also used this method to migrate a small disks content to a larger new one. Just resize the filesystems afterwards if needed.

cheers

---

### Post by ByteJuggler on 2008-07-31
> **c2olen said:**
> If you are just cloning your harddisk to another disk, there is no need to put in your blocksize. Make sure your target harddisk is at least the same size as the originating disk!
cheers

Yes as you say, its not *required*, ***however ***specifying a suitable blocksize can optimise the transfer speed.  You'll be surprised what a difference that can make.  Try it out with several block sizes, you'll see what I mean.

---

### Post by deamon_knight on 2008-08-01
So, lets say I'm doing something completely nuts, witha triple boot setup of XP/VISTA/UBUNTU, once I get everything installed. I can use:

dd if=/dev/hda of=/dev/"external HDD" 

or whatever, and then restore all partitions and boot info? That would be great!

---

### Post by ByteJuggler on 2008-08-01
> **deamon_knight said:**
> So, lets say I'm doing something completely nuts, witha triple boot setup of XP/VISTA/UBUNTU, once I get everything installed. I can use:

dd if=/dev/hda of=/dev/"external HDD" 

or whatever, and then restore all partitions and boot info? That would be great!

Correct.  :)  That would clone the entire disk, including partition table/mbr, and every partition (including each partition's boot sector) onto the other one.

Obviously the target disk must be at least as big as the source disk, and any space not used after the clone will have to be re-allocated/dealt with seperately after the cloning.

---

### Post by c2olen on 2008-08-01
> **ByteJuggler said:**
> Yes as you say, its not *required*, ***however ***specifying a suitable blocksize can optimise the transfer speed.  You'll be surprised what a difference that can make.  Try it out with several block sizes, you'll see what I mean.

I agree that using different blocksizes will get you better performance, depending on the application.
Because I was curious how much difference it would give ME I did some tests.
I ran several dd's against different blocksizes too what it would get me.

Below you can see the results.
I conducted a read-only test and a write-only test to get clear results.

This read-test result tells me that it does not make a lot of sense to figure out your optimal blocksize if you are pushing the limit of your controllers and or harddisks.
The results below give me the impression those limits are reached on my setup, which of course isn't that hard on a linux box.

[COLOR=Red]==Different blocksizes read-only on IDE Harddisk==[/COLOR]
acapulco:~# dd if=/dev/hda1 of=/dev/null bs=4k 
244983+1 records in
244983+1 records out
1003451904 bytes (1.0 GB) copied, 24.6419 s, 40.7 MB/s

acapulco:~# dd if=/dev/hda1 of=/dev/null bs=8k
122491+1 records in
122491+1 records out
1003451904 bytes (1.0 GB) copied, 27.2937 s, 36.8 MB/s

acapulco:~# dd if=/dev/hda1 of=/dev/null bs=16k
61245+1 records in
61245+1 records out
1003451904 bytes (1.0 GB) copied, 24.3508 s, 41.2 MB/s

acapulco:~# dd if=/dev/hda1 of=/dev/null bs=32k
30622+1 records in
30622+1 records out
1003451904 bytes (1.0 GB) copied, 25.1584 s, 39.9 MB/s

acapulco:~# dd if=/dev/hda1 of=/dev/null bs=64k
15311+1 records in
15311+1 records out
1003451904 bytes (1.0 GB) copied, 25.0736 s, 40.0 MB/s


[COLOR=Red]==Different blocksizes read-only on SATA Harddisk==[/COLOR]

acapulco:~# dd if=/dev/sda1 of=/dev/null count=100000       
100000+0 records in
100000+0 records out
51200000 bytes (51 MB) copied, 0.81559 s, 62.8 MB/s

acapulco:~# dd if=/dev/sda1 of=/dev/null count=10000 bs=4k
10000+0 records in
10000+0 records out
40960000 bytes (41 MB) copied, 0.651688 s, 62.9 MB/s

acapulco:~# dd if=/dev/sda1 of=/dev/null count=100000 bs=4k
100000+0 records in
100000+0 records out
409600000 bytes (410 MB) copied, 5.86529 s, 69.8 MB/s

acapulco:~# dd if=/dev/sda1 of=/dev/null count=100000 bs=8k
100000+0 records in
100000+0 records out
819200000 bytes (819 MB) copied, 12.873 s, 63.6 MB/s

acapulco:~# dd if=/dev/sda1 of=/dev/null count=100000 bs=16k
100000+0 records in
100000+0 records out
1638400000 bytes (1.6 GB) copied, 25.5734 s, 64.1 MB/s

acapulco:~# dd if=/dev/sda1 of=/dev/null count=50000 bs=32k
50000+0 records in
50000+0 records out
1638400000 bytes (1.6 GB) copied, 25.75 s, 63.6 MB/s
[COLOR=Red]
Of course I also had to do the write-only test.
== Write only test on a SATA disk based filesystem ==[/COLOR]

acapulco:~# dd of=/mnt/nasdata/test if=/dev/zero count=100000       
100000+0 records in
100000+0 records out
51200000 bytes (51 MB) copied, 0.607183 s, 84.3 MB/s  (DEFAULT BS=512b)

acapulco:~# dd of=/mnt/nasdata/test if=/dev/zero count=100000 bs=4k 
100000+0 records in
100000+0 records out
409600000 bytes (410 MB) copied, 6.70967 s, 61.0 MB/s

acapulco:~# dd of=/mnt/nasdata/test if=/dev/zero count=100000 bs=8k
100000+0 records in
100000+0 records out
819200000 bytes (819 MB) copied, 13.8758 s, 59.0 MB/s

acapulco:~# dd of=/mnt/nasdata/test if=/dev/zero count=100000 bs=16k
100000+0 records in
100000+0 records out
1638400000 bytes (1.6 GB) copied, 29.2223 s, 56.1 MB/s

acapulco:~# dd of=/mnt/nasdata/test if=/dev/zero count=100000 bs=32k
100000+0 records in
100000+0 records out
3276800000 bytes (3.3 GB) copied, 60.5215 s, 54.1 MB/s

This is of course not the most accurate way to test the different blocksizes, because the logical volumes blocksize itself doesn't necessarily match the blocksizes in this test, but it is clear to me the default 512b blocksize performs best for me. This doesn't this also applies to your setup.

This clearly demonstrates that the bs has to fit your hardware setup to get the best results.

---

### Post by cyclouno on 2008-08-01
Thanks all guys !!

Consider this example..

step 1
=====================
Original setup
=== 2 partitions
=== A - 100MB
    B - 100MB

=====================
step 2
====================
took backup using dd if=/dev/hda of=/dev/"external HDD"

================
step 3
===========
resize partitions

A - 150MB
B - 50MB

==================
step 4
==================
from recovery console, I Use the reverse dd command to copy the entire disk

dd if=/dev/"ext HDD" of=/dev/sda

==================
2 questions actually

Q1====will it automatically partition the disk & place contents in the corresponding parts??

Q2====should I put it into some DVD like this... 
dd if=/dev/sda of=/dev/"dvd-device" ????

---

### Post by prshah on 2008-08-01
> **cyclouno said:**
> Q2====should I put it into some DVD like this... 
dd if=/dev/sda of=/dev/"dvd-device" ????

No actually; this will become a multi-step process:

1) Create the image
2) Compress it to occupy less space (You will get space savings of _at least_ 50%), as well as split it into 4 GB chunks.
3) Get hold of the ["System Rescue CD"]("http://www.sysresccd.org/Main_Page") and create a customised bootable rescue CD following instructions from their site
4) Copy your hdd image to DVDs 
5) Keep the whole thing as a backup set.

One additional advantage if you're copying to DVDs; you can create archive files of 3.7Gb instead of 4 Gb; create iso's of each archive; then use a program called DVDisaster (it's in the repos) to create an error correction codec (ecc) that will make sure the DVD is accessible even if it is scratched or damaged (to a reasonable extent). You can then copy these iso images to DVD.

---

### Post by linux_tech on 2008-08-02
The nice thing about norton ghost is that it is fast.  Creating the image 
may take a small investment of an hour or so but sending the image or "multicasting" from 1 one machine or hard drive to another usually only takes 
10-15 minutes.  Then your OS, apps, etc. is back to its original state again.
Great for production environments.  Have a library of different images,
then multicast them out over the network to all your different machines. 
Another nice thing about it was you could also do hd to hd, just add a drive on the cable, boot to your cd or flash and initiate, that simple.

I just noticed they have a free ghost for linux available, so I'll give it a try and see what it can do. It looks to be available as iso or tar.gz

[http://linux.softpedia.com/get/System/Hardware/Ghost-for-Linux-053.shtml](http://linux.softpedia.com/get/System/Hardware/Ghost-for-Linux-053.shtml)

---

### Post by Maverynthia on 2008-08-02
What would be the steps to copy a hard drive to a bigger drive. I'm finding my 80G that came with my system is too small and thus are wanting to upgrade. You say it has to be dealt with seprately..how so? Basically I want to go from 80GBs:

40G Windoze XP~~
-----------------
1G /swap
17G /home
17G / 

TO:

125 Windoze XP~~
-----------------
1G /swap
120G /home
4G / <-- making that smaller Linux says I'm only using 2% of 17Gs so...no point in keeping it that big

How would I do this without borking any of the info, can the 'dd' command do this or would I need a different way?

---

### Post by cyclouno on 2008-08-02
> **prshah said:**
> No actually; this will become a multi-step process:

1) Create the image
2) Compress it to occupy less space (You will get space savings of _at least_ 50%), as well as split it into 4 GB chunks.
3) Get hold of the ["System Rescue CD"]("http://www.sysresccd.org/Main_Page") and create a customised bootable rescue CD following instructions from their site
4) Copy your hdd image to DVDs 
5) Keep the whole thing as a backup set.

One additional advantage if you're copying to DVDs; you can create archive files of 3.7Gb instead of 4 Gb; create iso's of each archive; then use a program called DVDisaster (it's in the repos) to create an error correction codec (ecc) that will make sure the DVD is accessible even if it is scratched or damaged (to a reasonable extent). You can then copy these iso images to DVD.

Simply loving it..:KS will try it & let you know.. btw did you read my question reg.. if my harddisk will be automatically partitioned to it's original sizes while I restore the Image contents?? 

Obviously I ain't talking about HAL !! It's just my sys - my backup / my sys - my restore.. :)

---

### Post by ByteJuggler on 2008-08-02
> **cyclouno said:**
> Simply loving it..:KS will try it & let you know.. btw did you read my question reg.. if my harddisk will be automatically partitioned to it's original sizes while I restore the Image contents?? 

Yes, that's correct, that's what will happen.  After the cloning onto the new drive, you will be left with unpartitioned space on the drive, equal to the difference in sizes between the old and new drives.  You can then use that as you see fit, e.g. by expaning the last partition into that free space, or by creating a new partition.

---

### Post by ByteJuggler on 2008-08-02
> **Maverynthia said:**
> What would be the steps to copy a hard drive to a bigger drive. I'm finding my 80G that came with my system is too small and thus are wanting to upgrade. You say it has to be dealt with seprately..how so? Basically I want to go from 80GBs:

40G Windoze XP~~
-----------------
1G /swap
17G /home
17G / 

TO:

125 Windoze XP~~
-----------------
1G /swap
120G /home
4G / <-- making that smaller Linux says I'm only using 2% of 17Gs so...no point in keeping it that big

How would I do this without borking any of the info, can the 'dd' command do this or would I need a different way?

You can use the "dd" command.  Simply image the entire source drive to your new drive.  Then swap around the drive id's (remove the old drive, put the new one in its place, and reboot from it.)  You'll have free unpartitioned space left over equal to the size of the new - old drive, which you can deal with as you see fit. (E.g. by creating another partition, or by expanding the last existing one into it etc.)

---

### Post by prshah on 2008-08-02
> **Maverynthia said:**
> What would be the steps to copy a hard drive to a bigger drive. 
How would I do this without borking any of the info, can the 'dd' command do this or would I need a different way?

In this case, I'd recommend you use partimage; it is GUI, far easier, safer and more convenient to use than dd.

```
sudo apt-get install partimage
```, then press Alt+F2, and give the command```
partimage
```

---

### Post by cyclouno on 2008-08-03
> **ByteJuggler said:**
> Yes, that's correct, that's what will happen.  After the cloning onto the new drive, you will be left with unpartitioned space on the drive, equal to the difference in sizes between the old and new drives.  You can then use that as you see fit, e.g. by expaning the last partition into that free space, or by creating a new partition.

BTW "dump" & "restore" commands are faster with the snapshot parameter???

---

### Post by Maverynthia on 2008-08-17
Partimage doesn't appear to be part of the LiveCD I have. I also have no space to save the images. I simply want to copy them anyways :/

Is there just no way to make a clone of a HD and resize as well?

Gparted only leaves the space at the end, which you can't resize for anythig at the front of the drive...

---

### Post by kushykush on 2008-09-18
How about guidance on copying the Ubuntu installation (partition) to another partition on the same or different hard disk. I tried copying my perfectly fine installation (partition) to another partition on a different hard drive through Ubuntu CD ("rescue a broken system option).  However, it did not copy my partition. Gave me errors and asked me to debug, which, of course, I cannot. 

Is there a direct way of copying your clean, working installation (partition) to another hard disk on the same computer?  I know it will disrupt the GRUB.  However, I can deal with it later once I am able to copy my installation.

---

### Post by prshah on 2008-09-18
> **kushykush said:**
> How about guidance on copying the Ubuntu installation (partition) to another partition on the same or different hard disk. I tried copying my perfectly fine installation (partition) to another partition on a different hard drive through Ubuntu CD ("rescue a broken system option).  However, it did not copy my partition. Gave me errors and asked me to debug, which, of course, I cannot. 

Is there a direct way of copying your clean, working installation (partition) to another hard disk on the same computer?  I know it will disrupt the GRUB.  However, I can deal with it later once I am able to copy my installation.

Copying the entire (working) partition to another partition using either "dd" and/or "partimage" or any of the other methods here should work just fine. If the copy fails, post the error messages for a clue.

You can also use "remastersys" to create a live CD  / backup CD of your (customized) installation, and use that.

Besides this, you will probably get a lot more responses if you use a new thread rather than recycle this old one.

---

### Post by kushykush on 2008-09-19
Thank you PRShah!
Could you tell me exactly how to make the backup CD. And once that is done, I can copy it on another partition??

---

