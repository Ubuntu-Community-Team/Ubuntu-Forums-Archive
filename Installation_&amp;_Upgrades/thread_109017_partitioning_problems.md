---
title: "partitioning problems"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2005-12-27
Hi all,
        I wanted to install Ubuntu 5.10.  I had a previous Suse Installation hence there was an ReiserFS filesystem. I wanted to revert back to ext3 file system. It's an 80 GB hard disk (76 Fomatted) with 60 GB divided into 7 partitions having Windows 98 on C:\, XP on D:\ the rest with data. All in Win95 FAT 32 as seen from fdisk -l from Linux. 
           The rest I wanted to keep for GNU/Linux in this fashion . 
/ - root for 12 GB
/home - for userspace 7 GB something 
swap - the rest/ remaining. 
          The first thing I did was deleting the existing partition.

 Then 
for root (/) :-

a. 12 GB gave it /, bootable flag & space from beginning of free space.

For user (/home) :-

b. 3 GB gave it /home, no bootable flag & space from ending of free space

 Till here it was fine. Then tried assigning the remaining 700 MB something which it was showing but the system wouldn't let me. It kept saying that this is unusable. I tried all kinds of different permutations/combinations to have 2 seperate partitions & a swap but was unsuccessful. Finally settled with / for 15.1 GB for / & the remaining 800 MB or so for swap. Was able to successfully load the desktop. After booting & playing around in Linux, reboot again & this time found out that my windowsXP bootspace somehow became corrupted & hence had to re-install the whole OS which obviously re-wrote the whole of boot-loader which I did later on from one of the webpages. 
       My questions are: -

Q1. When running the partition, if I had done the Ctrl+Alt+F1 would I've got a bash 
    console?

Q2. After deleting the partitions & making new partitions are there any tools with which I
    could check the health of the partition for bad sectors or something like this. 

Q3. Why was not I able to make the two partitions?

Q4. Any suggestions to improve the above path I had taken.

---

### Post by Herman on 2005-12-27
shirishag75, Did you pay attention to what the partition types were and where they were placed? 
By this I mean were they 'primary', 'extended', and 'logical'?
While we can place any type of partition anywhere, there are two rules that are important to keep in mind when partitioning.
 These are: 
*We can make four primary partitions, or three primary partitions plus one that is to be divided up into many logical partitions. Once a primary partition begins to be divided up in this way it is then called an 'extended' partition.
*We need to make sure all 'logical' partitions are one-after-the other like a chain, or maybe a train. A primary partition can be placed in between, but that will make any more logical partitions unable to be used. The link will be broken.

For these reasons, when anyone is making lots of partitions, it is wise to make the primary partitions at the begining of the hard drive or maybe one or two at the beginning and one or two at the opposite end. Normally, Windows likes to use primary partitions. If you do not need to use another primary partition yet, it is good to leave a space for it at one end or the other. This is not compulsory, but just an idea.
I think it is easiest to use the center of the hard drive, or the other end, for my extended partition, which contains all my logical partitions.
One extened partition may be divided up into as many as 63 logical partitions then (for IDE drives), or 15 (for scsi). It is simplest to just use a lot of logical partitions for Linux, as we can then create as many as we like, without any more worrying about the partitioning rules. 

I am not sure if this was what your problem was in this instance, since you didn't mention which partitions you had as primary or logical, but this advice might also help others reading the same post. :D (Herman)

---

### Post by Herman on 2005-12-27
>  Q1. When running the partition, if I had done the Ctrl+Alt+F1 would I've got a bash 
    console? [COLOR=Red]First, please read the Gnu Parted manual:[/COLOR]
   [http://www.gnu.org/software/parted/manual/]("http://www.gnu.org/software/parted/manual/")

[COLOR=Red][B]Gnu Parted is a powerful tool and should be used with extreme care.
[/B][/COLOR]
Using Parted from the Install CD

1) Boot with the Breezy Install CD

2) Allow it to proceed through the first stage (detecting hardware) until it stops at [!!] Partition Disks.
3) Press [Ctrl]+[Alt]+[F2]

4) Press [Enter] to activate console

5) Command:     #_[COLOR=Sienna]parted /dev/hda[/COLOR]

6) Command:    (parted)_ [COLOR=Sienna]print  [/COLOR]        (or just p for short)
               this will print out your current hard disk details.

7) Command:    (parted)_[COLOR=Sienna]h   [/COLOR]            ( for help )
               this will remind you of all the commands you can use.

[COLOR=Red]For more instructions please refer to the Gnu Parted manual:[/COLOR]
   [http://www.gnu.org/software/parted/manual/]("http://www.gnu.org/software/parted/manual/")
>  Q2. After deleting the partitions & making new partitions are there any tools with which I
could check the health of the partition for bad sectors or something like this.  8)You can use the command: (parted)_[COLOR=Sienna]check[/COLOR] 5     (or whatever number partition you want to check).
9) Command: (parted)_q             (Q for quit when you are finished), then exit to close Parted.

10)Then Command #_ reboot now             (to exit the command line interface).

>  Q4. Any suggestions to improve the above path I had taken. shirishag, it is up to you of course, but I don't understand why you want only 3.0 GB for /home, and allowed a whole 12.0 GB for / ?
If it was me, I would do the opposite, 12.0 GB for /home, and 3.0 for /
:D (Herman)

---

### Post by ShirishAg75 on 2005-12-28
[quote=Herman]
shirishag, it is up to you of course, but I don't understand why you want only 3.0 GB for /home, and allowed a whole 12.0 GB for / ?
If it was me, I would do the opposite, 12.0 GB for /home, and 3.0 for /
:D (Herman)[/quote]
Hi Herman, First of all thanx for replying. Would surely look up the manual for parted. Of course u'r right in saying in giving /home more space than /. My main motive is right now getting the understanding of partitioning right & then later to make a local repositery as given in the [https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto) & for this I suspect more space would be taken in the root rather than at the userspace level. I wouldn't be doing any server stuff or anything else. Just a normal guy who wants to constanly update his system, understand the system, Most of the stuff is in FAT32 partition which can be used by both systems. In event one of the systems/OS go down. Although now do have the ext2ifs system so can see the ext3 filesystem in windows. Thanx in advance.

---

### Post by Herman on 2005-12-28
Hi, shirishag75, okay, I understand you now, and I can see that you really know what you are doing. I am sure that when you take some time to read the manual you can get from the one of the links in the index page I linked you to, you will soon understand more than me about partitioning. That one is just the master link, and it leads to more links you can study. I have only recently begun to try to learn it myself. It has been a pleasure to be able to help you, shirishag75, and good luck with everything you do. If there is anything more I can help with, please ask, and I will certianly try my best for you.  :D (Herman)

---

### Post by ShirishAg75 on 2005-12-28
[quote=Herman]Hi, shirishag75, okay, I understand you now, and I can see that you really know what you are doing.(Herman)[/quote] On the contrary Herman I'm in the same boat as u & make oodles of mistakes (read typos here) hence it takes me twice the time to write clean as well as to understand the logic. Not a copy/paste kinda person but sometimes do get stumped.

[quote=Herman]I am sure that when you take some time to read the manual you can get from the one of the links in the index page I linked you to, you will soon understand more than me about partitioning. That one is just the master link, and it leads to more links you can study. I have only recently begun to try to learn it myself. It has been a pleasure to be able to help you, shirishag75, and good luck with everything you do. If there is anything more I can help with, please ask, and I will certianly try my best for you.  :D (Herman)[/quote]
     As far as the manual is concerned went through it, find it extremely non-user friendly. Although now understand little about how it works. Thank goodness the next time 6.04 there is talk of including GParted (Graphical partitioner). Also they need to make lots of changes to the default installer. One doesn't mind a text installer but needs to be better from usability perspective.

---

### Post by ShirishAg75 on 2005-12-29
Herman, would like to continue the parted thing here. For sure would be consulting the man again & again but sometimes discussing also puts some other perspectives or makes it more clear, so it would be good exercise. What do u think?

---

### Post by Herman on 2005-12-29
Okay then, shirishag75, can you see if you can get a copy of your output from using the 'print' command in parted, and tell me what it is you want to do and we can both decide on what is best then. I might need to sleep soon, a little bit, but I will look sometimes to see if you are posting something. (Herman) :D

---

