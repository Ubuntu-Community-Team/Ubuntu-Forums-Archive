---
title: "Install suggestions please..."
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by EldiS82 on 2009-04-19
Ok, as I am a quite newbie in this Ubuntu world I would like to have few suggestions at one place about the best way to install Ubuntu to fit my preferences.
I know you will say, ok, why don't you use search function, or google... I did but there is a bunch of different solutions, different suggestions, and so on. And we all expect something else of our system...

So to start...

1. I would like to keep my XP (for now) as there is still no perfect solution for running windows software on Ubuntu. And I mainly think about Adobe software. Yeah I know it works on this or that way but it's still buggy...
So I would lke to know what is the best way to install Ubuntu and to keep XP? Should I install it on the same partition beside XP, and if I do that, how stable is it as they are using different filesystems (is it possible at all)? Or should I install it inside the Windows? Or should I create new partition for Ubuntu and make clear installations of Ubuntu and XP on different partitions?

2. As I have one system and two "data" partitions (D & E) for now (one empty, one full), what should I do with filesystems on them after I install Ubuntu, cause I see that Ubuntu is able to read from NTFS but nothing more. And I don't want to lose data from one of them cause it's full. So is it smart choice to leave that partition as NTFS and to convert this empty one into ext3? And if I do that how is it works. Windows is not gonna recognise that partition at all, right?

3. I actually have two hard disks [C & D] and [E], so if I chose to install Ubuntu and XP on different hard disks, will I be able to dual boot then?

So my main dilema are those filesystems and how to fit some space for Ubuntu and some for XP.

Any suggestions?

---

### Post by groovete on 2009-04-19
Hi, 

it isn't important on which drive you will install ubuntu, there just has to be enough space.
I suppose that your c-partition is the full one, so I would take the entire e-drive for ubuntu. You don't have to format the drive in advance. Ubuntu will ask you and do it during the installation process.

If you aren't sure if you want to keep Ubuntu permanently, I would install it in Windows using the Wubi - Installer (D or E, doesn't make a difference).

Just insert the Ubuntu-CD when you are in Windows, than start the wubi.exe.

Afterwards you will have a dualboot using the windows boot manager. If you don't like Ubuntu you are able to uninstall it like any other windows programs.

BTW: You are able to read and write on an NTFS - partition from within Ubuntu! No problem! Windows isn't able to read an ext3 - partition. 

Regards

---

### Post by sumit.kalra999 on 2009-04-19
Hi,
If you are new to ubuntu, its better to install ubuntu inside windows. By this way, you can acces all the hard disk from both operating systems.

And you data will be safe. :-)

If you format your HD foranother file system, you have to do a lot of stuff like making backup of your data and then copying it back. 
And after that, windows xp will not able to read that file system.

---

### Post by spandon on 2009-04-19
Hi ELDiS82,
I have desktops and laptops all dual booting with either XP, Vista or Windows7 without any problems during the 4 years I have been using Ubuntu / Edubuntu from 5.04 up to 8.10 without being a "geek".
You do not state what size your empty partition/drive is, but this is how I install Ubuntu on my systems :
I create 2 partitions after the windows OS partition normally at the end of the disk of 10 and 2 gb (1 for Ubuntu and 1 for swap), I would create these partitions in your empty Partition/drive.
But, if you haven't tried the "Live session" of the version you intend installing, utilising the cd on the machine that you intend to install on - then please do so FIRST, making sure that everything works
Installing this way, I have never corrupted any of my Windows installations, but I have had a few corrupt mbr's which are easily repaired. details on how this is done are well documented on this forum.
Hope this helps
Don

---

### Post by zvacet on 2009-04-19
You can dual boot on one disc or you can use both discs.For first solution read [this.]("http://psychocats.s465.sureserver.com/ubuntu/dualboot") For dual boot on two HDD read [this.]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by EldiS82 on 2009-04-19
Thanks people...

Ok, this is what I could conclude after your suggestions (and after I downloaded Ubuntu Pocket Guide).

[And yes, I've tested Ubuntu 8.10 live session option and I'm blown away by the way Ubuntu looks]

By default my Windows partition is "C" (approx 25Gb) and on that HDD is another almost empty "D" partition (approx 55Gb).
And there is another HDD as a single "E" partition, which contains about 70Gb of data that I don't want to lose.

So maybe the best choice is to do a clean install of Ubuntu on this empty "D" partition and to use it in a future as a storage for ubuntu oriented software, files and so on... And from Ubuntu I will have acces to my files on ntfs "E" partition without any problems, right (writing, reading...)?

I hope I will report succesfull installing tonight/tomorrow, browsing with Ubuntu. :D

---

### Post by odinb on 2009-04-19
I did it another way when I had made up my mind to ditch windows....

Did a backup of all needed stuff on the C: drive, reformatted, installed Ubuntu using ext3.

Then I moved data over from one drive at a time, formatting to ext3 untill all drives on the system are ext3.

For my windows needs (yes due to stubborn monopoly companies I unfortunately also have them) I installed Win XP in virtualbox. After installing guest additions in vb, I can now map all needed drives in windows with full read/write access from windows even if they are ext3.

So now I can do my logitech Harmony updates and my Garmin nuvi updates in Win XP after configuring virualbox to always mount the remote/GPS to win XP when inserted.

For everything else there is linux/Ubuntu!

---

### Post by EldiS82 on 2009-04-19
Ta-daaa... :D

Ubuntu is now installed, without any problems. In the last moment I choose to repartition C and now there is 15Gb reserved for XP and 9Gb for Ubuntu...
For now I will leave other partitions in ntfs.

Only now it seems that I will not be able to setup connection that easy as I use an ancient dial-up modem. :(

Nevermind, soon I'm getting ADSL so I hope that then there will be no problems...

---

### Post by upchucky on 2009-04-19
you mentioned adobe and a need for it. if you are only reading adobe files, there are other solutions that are better, for windows there is the free Foxit reader, which uses half the resources and time that adobe uses, for any other things that are done with adobe there are other free alternatives.

the only thing i have found that I need win xp for is my magicjack phone service. but that is a work in progress and just a matter of time before it is ported to linux.

---

### Post by EldiS82 on 2009-04-19
No, no...
I mean Adobe software, not Adobe files...
Photoshop primarily, Dreamweaver, Audition, etc etc...

---

