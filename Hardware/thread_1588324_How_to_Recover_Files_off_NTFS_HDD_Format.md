---
title: "How to Recover Files off NTFS HDD Format?"
date: 2010-10-04
forum: Hardware
---

### Post by xovertheyearsx on 2010-10-04
Hi, I have a simple question. Looking for a honest, simple, direct answer.
----------------
-What Happened?-
----------------
A friend of mine wanted me to fix his corrupted OS and forgot to mention which files he needed backed up for his school and work projects. I ran in to few errors while trying to re-install Windows XP and figured I could do a Reverse Install, install Linux over Windows and then install Windows in to VMBox to figure out the specific errors. So I formatted his HDD without knowing he wanted his files backed-up. Now He has a Linux Partition which I created with Windows in VMBox.

-------------
-My Question-
-------------
I'd like to recover his files if at all possible. I am aware that the File System Format for Linux and Windows are different. But I also know that you can search through NTFS files with Linux, since I've done it before. I was wondering if there was any way I could recover his Art Portfolio (they're Images, Png, Jpg, Gif, etc) from the HDD I already formatted twice. I know it's a long shot, but Most Files do hang around. Any Takers?

-------------------------
-Computer Specifications-
-------------------------
Compaq Presario V3015NR Notebook PC
AMD TURION 64 X2 TL-50
1.6GHz, 256kb + 256kb L2 Cache
1024 MB DDR
80GB HDD

------------------
-COMPUTER HISTORY-
------------------
-> Windows XP
-----> Original Install, No Issues
-----> Unknown Corruption Issue... Mup.exe, Engine.dll Errors...
-----> OS Would Not Load...
-----> Safe Mode Failed...
-----> Did not run MiniXP...
-----> Did not run Recovery...
-----> (I thought it was a simple format and re-install job, i should have known better)...

-> Windows XP
-----> Formatted with NTFS QUICK FORMAT
-----> Windows Activation Successful (Faulty Key, Failed)
-----> Prompted to Re-Activate Windows, Windows Authetication Failed, 30 Day trial expired (after windows key registered through Phone and Online)
-----> Windows Activation Key Error

-> Linux Ubuntu 10.04.1
-----> Formatted SDA2 and SDA4 FULL SYSTEM FORMAT
-----> Created ext2 and ext4
-----> Clean Install, No Issues
-----> Installed 3rd Party Proprietary Drivers, No Issues
-----> Installed VMBOX Windows XP Home Edition 32bit
-----> Windows Activation Successful (Faulty Key, Failed)
-----> Windows Re-Activation Requested....
-----> Windows Activation Key Error

Btw... The Windows Key I'm using is from the Microsoft Certification Sticker Placed on the bottom of most Microsoft Computer Devices... This is a problem i already have a cure for.

I'd appreciate any help, Best Regards, AB

---

### Post by nevius on 2010-10-04
> **xovertheyearsx said:**
> Hi, I have a simple question. Looking for a honest, simple, direct answer.
----------------
-What Happened?-
----------------
A friend of mine wanted me to fix his corrupted OS and forgot to mention which files he needed backed up for his school and work projects. I ran in to few errors while trying to re-install Windows XP and figured I could do a Reverse Install, install Linux over Windows and then install Windows in to VMBox to figure out the specific errors. So I formatted his HDD without knowing he wanted his files backed-up. Now He has a Linux Partition which I created with Windows in VMBox.

-------------
-My Question-
-------------
I'd like to recover his files if at all possible. I am aware that the File System Format for Linux and Windows are different. But I also know that you can search through NTFS files with Linux, since I've done it before. I was wondering if there was any way I could recover his Art Portfolio (they're Images, Png, Jpg, Gif, etc) from the HDD I already formatted twice. I know it's a long shot, but Most Files do hang around. Any Takers?

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Check out testdisk and photorec.

For future reference, I always image a persons hard drive before working on the computer. Check out clonezilla.

The COA is for an OEM install. It may not work with whatever XP install disc you are using.

---

### Post by 23dornot23d on 2010-10-04
This would have probably been the way you could have recovered them[COLOR=Red] if no formating
and no overwriting of Data had occurred[/COLOR] ......

I doubt you stand any chance now .... as most of the DATA will be overwritten with the new
install ......

using [testdisk]("http://en.wikipedia.org/wiki/TestDisk") ...... to search and see if it can find the old layout .... of the disk

using [photorec]("http://en.wikipedia.org/wiki/PhotoRec") ..... to search for the files ......


But , after the formats and the addition of data to the drive - 

**I very much doubt that it is possible **.......

_____________________________________________________________

There are firms that can recover data off of drives ...... but highly unlikely if its been overwritten ......
as I would think that is not possible .......

How Big was the original Windows Partition .......... How much data was on it ............
Windows can be massive compared to Linux .... 

How much have you overwritten ........  was the Linux install just 4 Gig .....

I am really doubtful of any chance of success .........

[COLOR=Red][B]If my life depended on it ....... I would try a firm that specializes in data recovery ......
(but if you take this track .... do not do anymore work to the disk ....... you can only make it worse for them)
[/B][/COLOR]
If its not that important ....... then I would possibly try testdisk and analyze the disk
to see if it can see the old structure ...... long shot .....

If it could see the NTFS structure ..... 
I would then use TESTDISK and set it back to the NTFS structure ....
and then try to use photorec to see if it can find any files ........

[COLOR=Red]**These are such long shots though ........... **[/COLOR]
(someone else may be able to help ..... this is just my initial thoughts if it was my data)

That's the best advice I think I can give ....... that I think would give you a 
1 in a million chance at getting anything back ........

Hope this helps in some small way ........ chances are slim to non existent though IMHO

---

### Post by xovertheyearsx on 2010-10-04
> **23dornot23d said:**
> 
How Big was the original Windows Partition .......... How much data was on it ............
Windows can be massive compared to Linux .... 

How much have you overwritten ........  was the Linux install just 4 Gig .....

I am really doubtful of any chance of success .........

> **xovertheyearsx said:**
> 
------------------
-COMPUTER HISTORY-
------------------
-> Windows XP
-----> Original Install, No Issues
-----> Unknown Corruption Issue... Mup.exe, Engine.dll Errors...
-----> OS Would Not Load...
-----> Safe Mode Failed...
-----> Did not run MiniXP...
-----> Did not run Recovery...
-----> (I thought it was a simple format and re-install job, i should have known better)...

-> Windows XP
-----> Formatted with NTFS QUICK FORMAT
-----> Windows Activation Successful (Faulty Key, Failed)
-----> Prompted to Re-Activate Windows, Windows Authetication Failed, 30 Day trial expired (after windows key registered through Phone and Online)
-----> Windows Activation Key Error

-> Linux Ubuntu 10.04.1
-----> Formatted SDA2 and SDA4 FULL SYSTEM FORMAT
-----> Created ext2 and ext4
-----> Clean Install, No Issues
-----> Installed 3rd Party Proprietary Drivers, No Issues
-----> Installed VMBOX Windows XP Home Edition 32bit
-----> Windows Activation Successful (Faulty Key, Failed)
-----> Windows Re-Activation Requested....
-----> Windows Activation Key Error

Fully Formatted :( ...thanks guys, thats actually a better lead than i had before. I appreciate the help so far ;) ...I'm not too optimistic about the Recovery, i knows its a long shot. especially after multiple formats and OS installs.

---

### Post by xovertheyearsx on 2010-10-04
> **nevius said:**
> [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
For future reference, I always image a persons hard drive before working on the computer. Check out clonezilla.


Thanks, I deff. will take a look at this for future reference and use. ;)

---

### Post by 23dornot23d on 2010-10-04
That's a hard way to learn ... 
I always asked the customer to back up all their important data first .... if they cannot do it then I give them
help and also reminding them about photos - accounts .... messages memos etc .... need to be backed up .... school or college work should also be backed up by the user .... are no copies available on the school machine ..... was any of it uploaded to the web ....... the user needs a backup drive at least for things like that .......

Its so much easier nowadays to just add a USB drive ..... use a 1 terra USB drive 160 euros ...... someones data can be irreplaceable .....

Sorry .... I know its too late now .... but for next time ..... either get the person to backup all the data before you do any work ........ or ....... clone the disk to another before you start ..........

---

### Post by xovertheyearsx on 2010-10-04
> **23dornot23d said:**
> That's a hard way to learn ... 
I always asked the customer to back up all their important data first .... if they cannot do it then I give them
help and also reminding them... I asked and there was miss communication. I wasn't aware until after the format and install. And yes, it is a hard way to learn.
> **23dornot23d said:**
>  ...are no copies available on the school machine ..... was any of it uploaded to the web ....... the user needs a backup drive at least for things like that ....... Nope to all of the above. It was my friends personal computer. He isn't very tech savvy which is why he let me take it.
> **23dornot23d said:**
> 
Its so much easier nowadays to just add a USB drive ..... use a 1 terra USB drive 160 euros ...... someones data can be irreplaceable ..... Thats what i told him he should do. Just incase, you never know.
> **23dornot23d said:**
> 
Sorry .... I know its too late now .... but for next time ..... either get the person to backup all the data before you do any work ........ or ....... clone the disk to another before you start ..........
it's no problem. i gave him back his pc in working condition and he seems happy with it other than the fact he lost his data. he was excited about using linux since it has a lot of cool tools. so that actually cheered him up. he was thinking a mac, but then i introduced him to linux. of course i got windows working too on VMBOX. Thanks for your help, i had no idea that you could take images of HDDs.. its deff a tool ill be using in the future.

---

### Post by nevius on 2010-10-04
> **xovertheyearsx said:**
>  i had no idea that you could take images of HDDs.. its deff a tool ill be using in the future.

Just make sure to try it first on a computer that has proper backups. :)

---

### Post by 23dornot23d on 2010-10-05
> 
it's no problem. i gave him back his pc in working condition and he  seems happy with it other than the fact he lost his data. he was excited  about using linux since it has a lot of cool tools. so that actually  cheered him up. he was thinking a mac, but then i introduced him to  linux. of course i got windows working too on VMBOX. Thanks for your  help, i had no idea that you could take images of HDDs.. its deff a tool  ill be using in the future.
I always would make a separate copy of the USERS Documents and Settings Folder, often this will cover most of the things a Windows user will need back ..... and with Windows most of the programs they use are on CD - that may need to be put back ....

If the person is anything like me ...... if I ever loose things on the computer .... I set about reproducing them as good as I can at the time .... and the second time they often come out better ..... and as they say practice makes perfect.

Linux is such a good system to inspire people to learn more ...... and the freedom that comes with it promotes what people can do best ....... 

We work and do things because we get something back that some of the younger ones cannot see yet .... with Linux the person will become even more creative ....... 

Best of luck for your friend with the new setup ...... and choice is everything.

---

