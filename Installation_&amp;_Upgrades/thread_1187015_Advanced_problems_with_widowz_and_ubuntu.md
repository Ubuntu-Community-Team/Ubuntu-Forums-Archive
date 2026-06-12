---
title: "Advanced problems with widowz and ubuntu"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by icyfyer on 2009-06-14
hello,

i am an advanced user (in windows - midnovice in ubuntu). as such i have an advanced problem.

first the basics:
i have a dell mini 9 with the default 4GB STEC SSD. all of the other specifications are null as far as this post goes. being a netbook it obviously doesnt have a cd drive.
it came with ubuntu 8.04 dell netbook remix. as soon as i got it i installed xp from a USB flash drive. it worked flawlessly when i followed the instructions which are located here:

[http://www.pctipsbox.com/installing-windows-xp-using-a-usb-flash-drive/](http://www.pctipsbox.com/installing-windows-xp-using-a-usb-flash-drive/)

after using xp for a while i realized that i wanted to use ubuntu. i installed intrepid. i used it for a while but didnt like the audioplayers it had to offer, or the IM options, so i went back to xp. again, using the same USB method it worked without a problem. when it came out i installed jaunty. i like jaunty. but i still dont like the audioplayer options or the IM options in jaunty, so i want to go back to xp and use the persistent mode of jaunty most of the time so that i have in essence dual booting options. 

when i tried to install xp again using the same method, the exact same flash drive with the same software following the same instruction, i get this error:

"windows could not start because of a hardware configuration problem. could not read from the selected boot disk. check boot path and disk hardware. please check the windows documentation about hardware disk configuration and your hardware reference manuals for additional information."

to me, this means that the MBR is toasted. so the first thing i did was go back into the windows setup disk, choose the recovery option which gave me a command prompt, and do FIXMBR. that didnt work. i know that the MBR and the operating system are independent, so i tried reinstalling after doing the FIXMBR. that didnt work either.

next i did FIXBOOT. no dice. tried reinstalling after FIXBOOT didnt work either. 

then i tried using grub. i used the following instruction set:

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

when i do this command from inside grub:
find /grub/stage1
find /boot/grub/stage1
all i get is an error 15:file not found. so i sent this to google and came up with this page:

[http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261)

i tried some of the suggestions on this page, but nothing worked. i tried again with the "find" command and came up with nothing. i opened my grub menu.lst and it was completely blank. so i went back to this page:

[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

and tried to edit the list manually. this was my input:

 title Windows XP
grub boot menu
 rootnoverify (hd0,0)
 makeactive
 chainloader +1

since i am not dualbooting, i took the input from the example given for a real grub list on this page:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

that didnt work either. next i tried using gparted to delete and rebuild the partition table on the drive using this tutorial:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

i could format the drive to NTFS after that, but when i install windows i still get the same error about windows not being able to access the drive. 

my conclusion is so far that the drive cannot possibly be toasted, because i can still install ubuntu onto it just fine, but windows doesnt like it. i remember reading somewhere that windows and linux write differently to primary partitions and that once an inconsiderate OS is installed on a primary partition it is very difficult to get windows back onto that primary partition. maybe my memory tweaked some of that, so dont quote me. 

all i am looking for is a solution, or some suggestions to get this working without having to buy a new SSD. because i know this could become a problem for someone else, i would like to solve it completely, with as much detail as possible. if you need any further information, please ask, providing terminal code if necessary, and i will oblige.

---

### Post by ddrichardson on 2009-06-14
Sorry, are you getting this error from your USB boot disk or when Windows has been installed?

---

### Post by icyfyer on 2009-06-15
well, i get the error after i go through the initial part of the windows installation. if you have ever installed windowsxp, you know that it has to restar a few times before the installation is complete. the firs thing that happens is that one has to go through the text portion of the setup, which is where a partition is selected and possibly formatted. then the files are copied and the configuation for the GUI portion of the installation is set up. then the computer restars to bring up the GUI.

i am getting the error during this portion of the setup. if i select text mode, it of course takes me back to the initial setup where i have to choose the partition etc. but if i select GUI mode, it tries to initialize from the SSD and apparently cannot read from it.

i know the first thing you are probably thinking is "maybe the USB installation is fudged" but i know this; the installation is not at fault. i could not get this error any other way. i have tried formatting the drive and restarting the computer without any operating system and the results of this should be obvious; missing OS.

but again, i can still install linux with no problems...

---

### Post by icyfyer on 2009-06-15
thanks for your response by-the-way.

---

### Post by ddrichardson on 2009-06-15
Well, it's not the MBR because XP overwrites it after formatting the disk and you got past that stage. Will it let you in to the recovery console to do:```
bootcfg /rebuild
```

I also had a look in the MS KB: [http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

I'd be inclined to think that its worth checking the USB disk again, if it was unmounted at the wrong time then it might have corrupted one of the files listed (boot.ini would be my guess).  Also Ubuntu is pretty much a straight image copy rather than copying and extracting cabinets is stages so might be more forgiving on install - have you checked the SSD?

---

### Post by icyfyer on 2009-06-15
thanks for your fast responses.

yes, i was able to get to the recovery console. i did try the bootcfg /rebuild option a few minutes ago. that didnt work. i did, however come up with some good information. it seems that my boot.ini file is in good condition. when i did bootcfg /default i came up with this:

Microsoft Windows XP Professional
OS load options: /noexecute=optin /fastdetect
OS Location: C:\Windows

then, when i was playing with the settings in bios i eventually got some combination to give me this error:

Windows could not start because the following file is missing or corrupt:
<Windows Root>system32\hal.dll
Please re-install a copy of the above file.

so it looks like you are right about the MBR, and things are close to installing completely, but something is messing it up.

this is my plan now:
in the tutorial on how to install from USB the author says to restart the computer directly after the format is done. he says this is to make sure that the USB drive identifies correctly, or something. instead, i am going to just let it install without turning it off after partition and format. 

you dont have to respond unless you have a different idea. ill come back and post what the result is.

thanks for the link and the research.

---

### Post by ddrichardson on 2009-06-15
No worries dude - that makes sense, as Ubuntu uses UUID to identify drives at boot time - Windows doesn't.

---

### Post by icyfyer on 2009-06-18
so yeah, that didnt work. it installed like it has been doing, looked promising, then just gave me the same error as before.

i posed this question to the folks at mydellmini and one of them made the suggestion that i try doing CHKDSK /R under the windows recovery console. i tried it and of course i got the error that it is not installed, because windows was not completely/properly installed. is there a viable alternative to this in ubuntu? in case you dont know, CHKDSK /R is a function that scans the disk for errors and bad sectors, then attempts to repair them.

---

### Post by ddrichardson on 2009-06-18
testdisk but its not on the default Ubuntu install - it is on [System Rescue CD]("http://www.sysresccd.org/Download") (despite the name can be USB).

To save you asking if I know what stuff is in Windows, the answer is yes.  I've supported both for many, many years.

---

### Post by icyfyer on 2009-06-19
well, that sucks. is the rescue disk as intuitive as ubuntu?

---

### Post by icyfyer on 2009-06-19
here is some advice i am going to try in the meantime. it comes from a user named PALAWAN on the mydellmini forum.

icyfyer,
 
 ***running gparted and leaving the entire disk as unallocated didn't work for your windows installation? how about running gparted and deleting everything and creating a new partition table but assigning fat32 INSTEAD of ntfs for the whole disk/partition?***
 
when i was setting up my dual-boot os x winxp, i had problems with bartpe (windows pre-installation environment) not recognizing the partition table assignments created by gparted. i had the following listed partitions a. 200mb unallocated b. 14gb ntfs c. 200mb unallacated d. 15gb ntfs. i could not restore my backup (driveimage xml winxp backup) to either ntfs partition. consequently, i tried just running the winxp cd installation disk and it doesn't see the drive to install to.
 
the thing that worked for me is to change the ntfs partitions to fat32, then bartpe/driveimage xml could access either partitions.
 
having the whole drive as unallocated also allowed windows xp installation disc to see the drive...
 
if you haven't tried, please try to delete all partitions using gparted, **or** setting up the whole drive as fat32 using gparted and see if you can install the windows using either method.
 
i believe bartpe and winpe (the initial environment setup by windows xp cd during the installation process) has a problem reading an ntfs partition **created** by gparted.
 
good luck.

---

### Post by icyfyer on 2009-06-20
so that didnt work. i hope that no one ever has to search for this particular problem, because as it stands right now it looks like i have to replace my harddrive just to get around this problem. 

i won an ebay bid for a replacement drive, but it will take at least 2 weeks to get to me. in the meantime i am going to try downloading a copy of the rescue disk for ubuntu and scan the disk for errors. 

if you have any other advice, id like to hear it.

---

### Post by icyfyer on 2009-06-24
hers an update:

ERD Commander on USB works like a briliant charm. it installs very nicely and runs perfectly.

i was able to find my /dev/sda on my mini with ERD commander, and when i opened disk manager it told me that my partitions were unhealthy. so i formatted the linux partitions off of the drive and set it up with NTFS. and just to make sure, i deleted that partition and formatted to NTFS again. when i tried to reinstall XP on the drive.

NO GO.

it gives me abetter error this time though. there error is the please replace hal.dll. better than not being abe to read from the drive.

the next step is to copy all of the files inside the system32 folder of an operational machine and put them on my drive. i know that this is not a viable method to get an OS to work, but maybe the hal.dll file for the copy of windows that i am using actually is messed up. im sure it sitn because it worked fine before, but just in case. i have hacked it up with NLite so maybe it did something that the OS didnt like.

i dont know anything for sure. i just know that this problem is quite complex and i hope i solve it.

---

