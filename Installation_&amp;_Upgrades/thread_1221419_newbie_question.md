---
title: "newbie question"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by jokira247 on 2009-07-23
i have been windows user for 11 years now and i was thinking of trying linux and i chose ubuntu but i have a question i have 4 partitions and one of them is the c: which is 20gb for windows xp and the rest partitions are for data so can i formate this drive and install ubuntu on it without harming or formating the other partitions which contains all of my data?

another question is will i be able to view me ntfs partitions which contains my data in ubuntu?

---

### Post by sailthesea on 2009-07-23
You can only really have 4 primary partitions on a HDD Realistically you would have to use one of them for Ubuntu and possibly another as a swap although it wouldn't need to be very large If you have made a LiveCD to install from the GParted tool will do this from a live session Ubuntu can read NTFS drives but Windows does not read Ext
 Crucially remember to back everything up before any attempting anything and defragging your XP install a couple of times will help to make room
 Have a good read up and don't be afraid to post questions that may sound dumb we all started out in the same boat
 And Welcome:D

---

### Post by raymondh on 2009-07-23
> **jokira247 said:**
> i have been windows user for 11 years now and i was thinking of trying linux and i chose ubuntu but i have a question i have 4 partitions and one of them is the c: which is 20gb for windows xp and the rest partitions are for data so can i formate this drive and install ubuntu on it without harming or formating the other partitions which contains all of my data?

another question is will i be able to view me ntfs partitions which contains my data in ubuntu?

Hello and welcome.

You need a partition for Ubuntu and it can be an EXTENDED partition.  There is a [4 partition limit per HD]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition") (which you have right now) thus you need to make some decisions regarding those data partitions.

Another option for you (if you decide not to give up any existing partition) is to consider a [WUBI installation]("https://wiki.ubuntu.com/WubiGuide") which will make Ubuntu reside INSIDE your windows install (c:/drive).  Remember though that Ubuntu (in this case) will be exposed to the same performance issues as windows (i.e. fragemnted drive, etc., etc.).  Also, if your Xp crashes, so does your Ubuntu.

Ubuntu can read into NTFS using ntfs-config which is in the repositories.

---

### Post by jokira247 on 2009-07-23
this means if i chose not to leave the xp partition which is c: and use it completle for ubuntu the other three partitions will be safe or they will be formated also

ps: c: is primary and d,e,f are extended

---

### Post by raymondh on 2009-07-23
> **jokira247 said:**
> this means if i chose not to leave the xp partition which is c: and use it completle for ubuntu the other three partitions will be safe or they will be formated also

ps: c: is primary and d,e,f are extended

I recommend dual-boot until you are ready and comfortable with Ubuntu/Linux. Can you spare at least 15GB for Ubuntu?  Maybe move some data from one partition to another to free up the space?

In the end, it's your choice.  Yes, if you reformat **JUST** the XP partition, you will only erase XP.  The installer will give you option which partition to install Ubuntu.

Remember ... windows-based programs and applications (if you consider them data) cannot be run under Ubuntu unless you use wine or virtualization.

---

### Post by KinKiac on 2009-07-23
You can format each partition separately, so no, your data partitions wont be affected or shouldnt be if you dont touch them.  What you can do if you are willing to get rid of XP is simply delete that partition, then repartition say 1gig or so as swap(the installer for ubuntu should be able to do this, and then format the rest of the partition as ext3 or ext4, whichever you prefer(Im too new to know the pros and cons of the 2).  You'll then use the new partition to install your Ubuntu. 
 
My system is set up in a similar manner and this is basically what I did.  The only difference is that I have 2 drives, 1 has my Windows on it, and the other has 3 100 gig partitions.  I have always used my 3 100g partitions to store all my data and files(I tried not to store anything on C if I could avoid it).  So, when I went to install ubuntu I just cleaned up one of my partitions, then when installing ubuntu I deleted the empty partition and created 2 new ones with the empty space, one swap and one ext3, installed on ext3 and I was good to go.  I didnt even have to install the NTFS support to at least read my other partitions after install.  Ubuntu even recognized them and placed in my places menu, although it didnt mount them until I tried accessing them, in which case it mounted automatically.  

So far Im very impressed and would have gotten rid of my windows altogether if it wasnt for my GF.  

Good Luck with your install and as others have mentioned Welcome!

---

### Post by raymondh on 2009-07-23
quick question...

D, E & F ... are they logical partitions inside an EXTENDED or ... are each of them separate (individual) extended partitions?

---

### Post by sailthesea on 2009-07-23
> **jokira247 said:**
> this means if i chose not to leave the xp partition which is c: and use it completle for ubuntu the other three partitions will be safe or they will be formated also

ps: c: is primary and d,e,f are extended

You can install ubuntu over XP if you wish just be very careful to follow the installation instructions you must only install manually in the C partition 
D,E and F are your data and recovery partitions as setup by XP and if you overwrite them you lose everything
 Using Wubi wouldn't be a bad idea to see how things work or you could go down the road of a Dual boot system 
 As said backup before you try anything
 Do you have a LiveCD to try out? It would help figure out your system and let you get more help with your install

---

### Post by jokira247 on 2009-07-24
thanks to all of u mates u are really a great community

---

