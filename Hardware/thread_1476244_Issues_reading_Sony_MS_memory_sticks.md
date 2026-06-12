---
title: "Issues reading Sony MS memory sticks"
date: 2010-05-07
forum: Hardware
---

### Post by Phosphorror on 2010-05-07
Greetings all,

I have installed Ubuntu 10.4LTS and have completely ditched with Windows 7 install and moved to this platform. So far, all is very good indeed and I am loving this shiny new o/s.

BUT...there is a quibble...

I am having issues with the memory card reader in the PC. It doesn't show up all the options available.

Go to places>computer> and I see:
CD/DVD Drive
Generic Flash HS-CF
Generic Flash HS-MS/SD
Generic Flash HS-SM
File System

Upon insertion of the memory card 'Generic Flash HS-MS/SD' disappears without trace. I was after transferring pictures from a Sony Memory Stick PRO Duo (8gb) onto Ubuntu this evening, but alas, no joy.

The PC has a built in card reader called 'Connect XL' 

The PC is a Medion Akoya E4355D (MD 8341). Intel i3 processor with 3gb of RAM. It's an Aldi OEM PC that had Windows 7 but I wiped it for Ubuntu 10.4LTS which has been a great experience apart from this fly in the ointment.

I look forward to your help on this matter. Many thanks.

---

### Post by tgalati4 on 2010-05-07
Start with a clean boot.
Open a terminal.
Insert your sony mem stick.

dmesg | tail -50

Post the output from above.

---

### Post by Phosphorror on 2010-05-07
The results are as follows:

[  208.219141] sd 6:0:0:1: [sdc] Unhandled sense code
[  208.219146] sd 6:0:0:1: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  208.219151] sd 6:0:0:1: [sdc] Sense Key : Medium Error [current] 
[  208.219156] sd 6:0:0:1: [sdc] Add. Sense: Unrecovered read error
[  208.219162] sd 6:0:0:1: [sdc] CDB: Read(10): 28 00 00 63 3f 60 00 00 08 00
[  208.219173] end_request: I/O error, dev sdc, sector 6504288
[  211.275161] sd 6:0:0:1: [sdc] Unhandled sense code
[  211.275165] sd 6:0:0:1: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  211.275170] sd 6:0:0:1: [sdc] Sense Key : Medium Error [current] 
[  211.275175] sd 6:0:0:1: [sdc] Add. Sense: Unrecovered read error
[  211.275181] sd 6:0:0:1: [sdc] CDB: Read(10): 28 00 00 0c e7 f8 00 00 48 00
[  211.275192] end_request: I/O error, dev sdc, sector 845816
[  211.275197] __ratelimit: 26 callbacks suppressed
[  211.275200] Buffer I/O error on device sdc1, logical block 422812
[  211.275205] Buffer I/O error on device sdc1, logical block 422813
[  211.275208] Buffer I/O error on device sdc1, logical block 422814
[  211.275212] Buffer I/O error on device sdc1, logical block 422815
[  211.275218] Buffer I/O error on device sdc1, logical block 422816
[  211.275222] Buffer I/O error on device sdc1, logical block 422817
[  211.275225] Buffer I/O error on device sdc1, logical block 422818
[  211.275228] Buffer I/O error on device sdc1, logical block 422819
[  211.275232] Buffer I/O error on device sdc1, logical block 422820
[  211.275235] Buffer I/O error on device sdc1, logical block 422821
[  214.318190] sd 6:0:0:1: [sdc] Unhandled sense code
[  214.318196] sd 6:0:0:1: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  214.318202] sd 6:0:0:1: [sdc] Sense Key : Medium Error [current] 
[  214.318209] sd 6:0:0:1: [sdc] Add. Sense: Unrecovered read error
[  214.318216] sd 6:0:0:1: [sdc] CDB: Read(10): 28 00 00 0c e7 f8 00 00 08 00
[  214.318231] end_request: I/O error, dev sdc, sector 845816
[  217.361985] sd 6:0:0:1: [sdc] Unhandled sense code
[  217.361989] sd 6:0:0:1: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  217.361994] sd 6:0:0:1: [sdc] Sense Key : Medium Error [current] 
[  217.362000] sd 6:0:0:1: [sdc] Add. Sense: Unrecovered read error
[  217.362005] sd 6:0:0:1: [sdc] CDB: Read(10): 28 00 00 00 00 d8 00 00 08 00
[  217.362016] end_request: I/O error, dev sdc, sector 216
[  217.362021] __ratelimit: 30 callbacks suppressed
[  217.362025] Buffer I/O error on device sdc1, logical block 12
[  217.362029] Buffer I/O error on device sdc1, logical block 13
[  217.362032] Buffer I/O error on device sdc1, logical block 14
[  217.362035] Buffer I/O error on device sdc1, logical block 15
[  220.405662] sd 6:0:0:1: [sdc] Unhandled sense code
[  220.405667] sd 6:0:0:1: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  220.405672] sd 6:0:0:1: [sdc] Sense Key : Medium Error [current] 
[  220.405677] sd 6:0:0:1: [sdc] Add. Sense: Unrecovered read error
[  220.405683] sd 6:0:0:1: [sdc] CDB: Read(10): 28 00 00 00 00 d8 00 00 08 00
[  220.405694] end_request: I/O error, dev sdc, sector 216
[  220.405701] Buffer I/O error on device sdc1, logical block 12
[  220.405706] Buffer I/O error on device sdc1, logical block 13
[  220.405709] Buffer I/O error on device sdc1, logical block 14
[  220.405712] Buffer I/O error on device sdc1, logical block 15

---

### Post by tgalati4 on 2010-05-07
Not good.  Either your card has developed a problem, or your built-in reader can't read 8 GB cards.  Did it work under windows?  Do you have any smaller cards? If so then try reading a smaller card.

Whatever you do, don't format it under linux because it will mess up the heads, cylinders, sectors count.  Your best bet is to put it in a Sony phone, TV, mp3 player and see if you can see the files.  Try to recover the files on another machine and reformat inside a camera or other Sony device.

---

### Post by Nightstrike2009 on 2010-05-08
Hiya tgalati4;

> Whatever you do, don't format it under linux because it will mess up the heads, cylinders, sectors count. Your best bet is to put it in a Sony phone, TV, mp3 player and see if you can see the files. Try to recover the files on another machine and reformat inside a camera or other Sony device.

Although this advice is sound what would you do if you only have one machine running Ubuntu?  Phosphorror runs ubuntu only and I am a dual-booter like Phosphorror I wish to migrate to Ubuntu fully (and not use windows at all), is this advice aimed at not losing data or would it just not work at all after an ubuntu format? Has far as I know it works on Windows so the fault shouldn't be a reader problem (unless it is reliant on Windows software)

My memory card reader works fine on my machine Sandisk Imagemate 12 in 1 (SDDR-89) and have no issues with any card.

PS: I know Phosphorror from outside of the forums hence the extra info, I was one of the people who introduced him Phosphorror to Ubuntu. I don't seek to patronise just to learn more so I can ditch windows fully (if possible) :-)

---

### Post by Phosphorror on 2010-05-08
Fortunately for me, my MAIN machine runs Lucid Lynx and my Notebook runs Windows XP/Jaunty Jackalope so it's not too much of a problem.

It's just odd how Ubuntu hates it straight from the off. yet in Windows it was fine.

I do understand that it does have a different file structure so it wouldn't be a good idea to format it under Linux as suggested by  tgalati4.

The card had 2 garbled pictures on it, when I came back from a gig when it was last looked at under Windows a couple of weeks ago and I deleted the pics in question and it viewed the rest of the card fine.

Anyway, I shall copy the data on the XP side of the Notebook and format the card in the camera as suggested. Many thanks.

---

### Post by Nightstrike2009 on 2010-05-08
Glad you can get it sorted mate, however;

I don't see that has a fix for Ubuntu only machines unless it is suggested that all Sony MS memory stick hardware is avoided on Ubuntu. All my tech has SD cards so probably won't suffer that problem but what about PSP owners and others with Sony MS memory stick equipped hardware?

You would think their would be a utility for this purpose available on ubuntu as it seems a big flaw for such a elegant OS?

---

### Post by tgalati4 on 2010-05-08
You can format it in linux, but you must match the original CHS count.

Try reading it with gparted.  It probably doesn't have a vaild partition table.  Once you add a partition table, linux should be able  to read it.  Cameras and Windows ignore partition tables  on mem sticks.

---

### Post by Nightstrike2009 on 2010-05-09
Thanks for the advice tgalati4,

I did think of gparted but was unsure as its main purpose is a partition manager for hard drives.

Is there not a ubuntu equivalent of the M$ "Scandisk" program that could do the job available?

Your advice is correct and trusted I just find it hard to accept that such an "elegant" OS such as Ubuntu lacks a "Scandisk" type utility for solving such problems.  Using a Virtualboxed "Windows XP" would get around the issue but seems a little OTT just for a corrupt memory card.

---

### Post by Nightstrike2009 on 2010-05-09
Just discovered this thread link by **digital_sabotage **[http://ubuntuforums.org/showthread.php?t=121134]("http://ubuntuforums.org/showthread.php?t=121134") it refers to Ubuntu 9.10 but sheds some light on the issue. :-)
the reply **By Bscbrit** may lead to an answer of sorts

> **By Bscbrit:**For a 'scandisk' equivalent, look at 'man fsck' on the command line. However, you will find that the system will automatically carry out a 'fsck' (file system check) every so often (perhaps every 24 boots or so). Other than that, the need to carry out your own fsck is a rare thing indeed unless you are in the habit of switching off your computer without letting the system shut down for you.

Maybe if you navigated to the drive in terminal and ran this command it may repair it (this is in theory not practiced, yet)

Also found this: [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery") from Ubuntu community documentation which mentions a utility called *GNU ddrescue  (packaged as gddrescue) *

PS: I am clutching at straws and using Google to search for information but just trying to resolve this issue within Ubuntu. :-)

---

### Post by tgalati4 on 2010-05-09
There are lots of tools available, but you need some experience with them.  I have messed up some SD cards while reformatting them in Linux.  I have also rescued some similar cards by formatting them with the correct chs count.

[http://ubuntuforums.org/showthread.php?t=1245694&highlight=format+sd+cylinder+sector+head&page=2](http://ubuntuforums.org/showthread.php?t=1245694&highlight=format+sd+cylinder+sector+head&page=2)

[http://ubuntuforums.org/showthread.php?t=1204308&highlight=format+sd+cylinder+sector+head](http://ubuntuforums.org/showthread.php?t=1204308&highlight=format+sd+cylinder+sector+head)

Sometimes a simple workaround is to put the card in a Sony camera or cell phone and then plug that into USB.  Then you can access the card.  It's a little slower that way, but it usually works.

---

### Post by Nightstrike2009 on 2010-05-10
Heard of a program reccommended by **dino99** "testdisk"

its in repos so in terminal:
> 
sudo apt-get install testdisk

when installed just type:

> sudo testdisk

in terminal to run, i've no idea how its used, though "(create) Create a new log file", then select drive seems the way forward

A new thread asking help has been created to deal with this by myself [http://ubuntuforums.org/showthread.php?t=1478938]("http://ubuntuforums.org/showthread.php?t=1478938") lets hope we get the answers we seek

---

### Post by Phosphorror on 2010-05-10
Cheers guys, very helpful stuff. 

I am just glad its not a Ubuntu error, or Ubuntu hating my built in card reader, and that if all else fails check it on a Windows PC.

Mind you, a scandisk alternative would be rather nice. And I shall check them out and see how I go on.

---

### Post by Nightstrike2009 on 2010-05-13
I reccomend downloading the Virtualbox deb > [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and virtualizing Windows XP on Ubuntu its far easier that you think.

The Ubuntu alternatives seem too complex (to scandisk), but always seek out a linux version before relying on WINE or Virtualisers. 

Linux native programs work better on Ubuntu in most cases(Obviously).

---

### Post by mh2ack on 2010-05-16
I found a simple issue that may be at play here. Using several different  Memory Stick Pro Duo cards in a couple different card readers, I found  that I could read some but not others. I had been able to read all of  them with Ubuntu 8.04. I had just recently wiped my system and installed  Ubuntu 10.04 which is when I encountered the problem. I tried reading  the same cards with Ubuntu 9.10 and got the same results. The suggestion  to use gparted got me to thinking. I went to System/Administration/Disk  Utility and discovered that the problem is how the card is formated.  The cards that I can not read are in FAT12. The ones that do read are in  FAT16. So evidently FAT12 is no longer supported by Ubuntu. This is  something folks at Ubuntu need to be aware of. Just thought everyone  might like to know that there really is nothing wrong with your Memory  Stick Pro Duo cards. You just need to reformat them to FAT16 to make  them readable to your Ubuntu computer. Or you could install in  VirtualBox an older version of Ubuntu that does read FAT12. Its just as  likely to work as installing MS Windows and not cost you $$$. Just might  want to make certain that FAT16 is supported by your  cellphone/camera/device.

---

### Post by DavidVS on 2010-08-21
> **mh2ack said:**
> ...So evidently FAT12 is no longer supported by Ubuntu. This is  something folks at Ubuntu need to be aware of. Just thought everyone  might like to know that there really is nothing wrong with your Memory  Stick Pro Duo cards. You just need to reformat them to FAT16 to make  them readable to your Ubuntu computer.

Thank you for discovering what is causing problems!

How do I take this advice and format my Memory  Stick Pro Duo card as FAT16?  (My family has a Windows computer, so I can do use that if doing so makes this task easier.)

For the record, my computer is running Ubuntu 10.04 and does not see my Memory  Stick Pro Duo card at all.

Thanks you for any help,
 David V.S.

---

### Post by Rodney9 on 2012-02-08
Wrong Post

---

