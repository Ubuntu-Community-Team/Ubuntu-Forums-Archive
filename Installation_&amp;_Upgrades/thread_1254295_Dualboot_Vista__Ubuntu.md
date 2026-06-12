---
title: "Dualboot Vista / Ubuntu"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by Trimex on 2009-08-31
Hi :)
my first post ever on this forum ^^, but i need you guys help :)

i got now vista ultimate, and i want to dualboot ubuntu with it.

i follow the guidelines to do that , but then the problem starts.

ok, so i need to shrink my c:
thats not a problem and i got a 11GB emty space.
[IMG]http://i26.tinypic.com/1183g4k.jpg[/IMG]

at the guideline that im using it says to choose the following option:use the largest continous free space
[IMG]http://apcmag.com/images/howto/dualboot_ubuntu_vista_vista_first/ubuntu_install_05.png[/IMG]

but my problem is now, i can't select that because its not there :s.

and when i select specify partition manualy, i cannot choose that free space.

how can i use that free space ?
do i need to give that free space a letter like u: ? so its more visable ?
and if i give that free space the lettre u:, would i stli be able later to put c: and u: back togheter ?

ty Trimex :)

---

### Post by Partyboi2 on 2009-08-31
Hi, you can only have 4 primary partitions, are they all primary partitions that you have? If so you will need to create a extended partition.

---

### Post by Trimex on 2009-08-31
> **Partyboi2 said:**
> Hi, you can only have 4 primary partitions, are they all primary partitions that you have? If so you will need to create a extended partition.

hi, i can only use the c: and d: partition, the first one and the last one (3gb and 9,7gb),, i cannot use, and where there from in the beginning and i dont know what they are for.

and how do i create a extended partition?

ty :)

---

### Post by Trimex on 2009-08-31
bump

srry, but i really need the answer :s

---

### Post by stlsaint on 2009-08-31
well you can create the extend partition thru vista but i suggest combining some of them ol partitons that you arent sure what they are used for and maybe using it. but yes you can either use the livecd or create it using vista.

---

### Post by Bartender on 2009-08-31
I've suggested this many times for Acers, so I hope nobody minds me doing it again.
If you haven't burned your recovery DVD's do so now.  Buy a handful of the best quality DVD-R media you can and go thru the steps to make the DVD's.

I realize this is a hard thing to do to a perfectly good laptop, but run the recovery DVD's.  

I had the same problem with our Acer 5920.  4 primary partitions.  After running the recovery DVD's there was only one primary partition.  Installing Ubuntu was then a simple process.

Here's how I would do it nowadays - 
1) Burn the recovery DVD's.
2) Burn a GPartedLiveCD.  Make sure it will boot the laptop and get to the partitioner map.
3) Delete all partitions.
4) Create an NTFS primary partition out of half (or one-third or whatever you choose) of total disk space.
5) The Vista recovery DVD's will only see the NTFS partition and install to that area.  The rest of the drive is free for Ubuntu without trying to shove Vista over.

---

### Post by Mark Phelps on 2009-08-31
I appreciate your enthusiasm in wanting to try Ubuntu, but if you mess up your partitions, you'll end up with an electric brick.

So, you should ensure that you have the means to recover your Vista installation before you begin.

The steps you will need to follow are:
1) Use the Vista Disk Management utility to shrink the Vista OS
2) Reboot to confirm that worked OK
3) Use the same utility to move the NTFS partitions after Vista to the left to make room for Ubuntu
4) Reboot to make sure that worked OK
5) Boot into the Ubuntu Live CD and use the Partition Editor to create your Ubuntu partitions in the free space.
6) Boot using the Ubuntu LiveCd and choose manual partitioning to reuse the partitions you just created.

If you allow Ubuntu to resize your partitions, you run the risk of corrupting the Vista OS.

If this all sounds too complicated, you should consider using Wubi to install Ubuntu inside Windows to try it out.  IF it works well, there are instructions available for moving that to its own partition later.

---

### Post by Trimex on 2009-08-31
ok, il see what i can do :)
ty all for repliing ;)

---

### Post by Bartender on 2009-09-01
RE: Mark Phelp's advice -
I don't think you can add an extended partition to a HDD that has four primary partitions.

From wikipedia: *"The total data storage space of a PC hard disk is divided into at most four, and at least one, primary partitions. One of these can also be an extended partition."*

---

### Post by Topsiho on 2009-09-01
Bartender is right.

If you need more than 4 partitions you should make one of them an extended partition. This extended partition then can be used as a container for a quite enough (16?) number of logical partitions (numbered sda5, sda6, etc.) which you can use as usual.

Topsiho

---

### Post by Mark Phelps on 2009-09-01
> **Bartender said:**
> RE: Mark Phelp's advice -
I don't think you can add an extended partition to a HDD that has four primary partitions.

Yeah, I know that -- but I counted five partitions in the screen shot, so I presumed that the OP already had an extended partition in there somewhere.

But you're right -- if they're all primary, that makes the job much harder since two of them will have to be saved offline, removed, recreated inside an extended partition, and reloaded from the offline backup.

---

### Post by fonsi2099 on 2009-09-09
Help, I can not install XP on my HP- Labtop. now I'm working with Jaunty, I need to install XP, because I want to abort to work with Vista, after start the installation I get the ***STOP: 0x0000007B (0xFFF... ), I formated the  vista partition with G parted , and I still getting the same error.. is there any way to solve this problem? nd install XP instead vista.  I need MS XP for some applications for my home office. thanks for any hepl :(

---

