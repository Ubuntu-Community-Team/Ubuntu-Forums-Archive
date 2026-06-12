---
title: "problems upon upgrading jaunty"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by king2007 on 2009-04-18
How did i mess up my system ? As mentioned upgrading failed - to be expected since i am too eager - the official release is only within five days i guess. Now i want to use ubuntu (very appealing) and do so since gutsy gibbon - upgrading to hardy heron was also very problematic as i recall from last year. however i managed to download the .iso-image of jaunty, burnt it succesfully and tried to take it from there. booting failed so i read and read again and read everywhere and tried to use the supergrubdisk from april 2008. from live swap to double swap and single swap again and over again...... one needs windows again to download bcd.exe for example as well as : unetbootin-supergrubdiskrev120.exe.....
Now i have three discs : one with xp in use since 2006 (lot of data !) which is not transferred yet all to ubuntu 
- second one with ubuntu's on it (sacrificed by my wife) and a third one which is solely used by my wife. i also had vista on the first disc which i upgraded to windows 7. in order to be able to boot again i re-installed windows xp on the first disc without succes. i managed to get into a dos-command-window, but my knowledge is insufficient. as is with the command-line in ubuntu. so i figured, when i delete the partitions with windows 7 on it - the vista-disc says simply 'you are not allowed to repair' and the windows xp-disc is not very helpful either with regards to booting-up i deleted the re-install of xp and another logical part which was called dev/sda3 'f w95 ext'd LBA'.
for instance : what is the difference between "sudo fdisk -lu" 
and "sudo fdisk -l" ? anyone or meierfra. ?
output is as follows : otto@otto-desktop:~$ sudo fdisk -lu
[sudo] password for otto: 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfad0fad0
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   281426669   140713303+   7  HPFS/NTFS

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8ac243fa
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   314167139   157083538+  83  Linux
/dev/sdb2       314167140   320159384     2996122+   5  Extended
/dev/sdb5       314167203   320159384     2996091   82  Linux swap / Solaris
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x912f2252
Would somebody be so kind to guide me into booting into windows again so i can proceed transferring data ? thanks in advance !

---

### Post by Herman on 2009-04-18
> for instance : what is the difference between "sudo fdisk -lu" 
and "sudo fdisk -l" ? 
With 'sudo fdisk -l', the output tells us which cylinder the partitions start and end on.
It is presumed that partitions will start and end on a cylinder boundary.
Each 'cylinder' is 63 sectors. Each sector can hold 512 bytes of information.

When we use 'sudo fdisk -lu', the output is in sectors.
We can see what sector our partitions start and end on. So it's more precise. 
Nowadays not all partitions start and end on cylinder boundaries, new technology may cause that to change but no-one knows for sure yet.

---

### Post by king2007 on 2009-04-18
Thanks Herman ! With Gparted the partition editor told me the first disc could NOT be checked and i was advised to rund CHKDSK /F on ....
windows 
then reboot twice ?

---

### Post by Herman on 2009-04-18
Yes, GParted can sometimes do a kind of file system check in your NTFS partition, but I think it will only do so if your NTFS file system is already in reasonable shape.
The ntfsprogs developers are doing a great job coming to terms with the NT File System, but at this point in time we are still much better of to use Windows' own tools to do a proper file system check in your Windows NTFS file system.
I don't know why it advised you to reboot twice. Probably it would be best to just do what it says.

So, if I understand your story, you had Windows XP in partition 1 of your first hard disk and it has remained there since you first installed it back in 2006, and it contains a lot of data.
You installed Windows Vista after XP and it kindly donated its boot loader, 'BCD', to the Windows XP installation in the primary partition. That made Windows XP the 'boot partition' for Vista.
Later, you upgraded from Vista to Windows 7.
Then for some reason you couldn't boot either Windows 7 or XP?
So you overwrote Windows 7 with another Windows XP installation in the hopes of being able to boot your original XP system through that?
That didn't work either, so you deleted it and you're still trying to fix the Vista BCD loader that's stuck in your original Windows XP system?
I think I understand what you mean. . .  :-k

Well, for now you can probably boot Windows XP right away or anytime with one of these neat NTLDR boot discs which you can download for free from Miles Comer's site,  [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm")[U].
[/U]Those boot discs are really great and they'll boot Windows XP almost no matter what.
Then when you get it booted, you can delete the BCD files since you don't want them. (delete a file called bootmgr and a folder called boot).
If you still have NTLDR, NTDetect.com and boot.ini, it would probably be best to leave the original copies of those files alone. Those are your Windows XP's vital boot loader files.
If you don't have a copy of NTLDR, NTDetect,com and boot.ini there anywhere, (remaining from before you installed Vista), you can always copy those files off the CD. You can't boot Windows XP without those three files, (except if you have BCD and BCD works for you).

After that, you should be able to boot your Windows XP 'Installation' CD, and run FIXBOOT, and after that GRUB should be able to chainload Windows for you. 
If you want to be able to boot Windows XP by itself, you can run FIXMBR too.

That should get your original Windows XP back to normal again, (if you had to copy in a new boot.ini, you might need to edit it to get the boot menu back to normal).

Or, you might re-install Windows7, it should overwrite the old BCD and fix things so you can boot both systems, but I guess you don't want to do that, or you already tried that and it didn't work.

---

### Post by Herman on 2009-04-18
Here's a link about how to use the Windows XP 'Recovery Console', just in case you need it, [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm").

That's to help you run CHKDSK or FIXBOOT or FIXMBR, you probably know that already but I thought I'd add the link here to make sure.

---

### Post by king2007 on 2009-04-19
Hello Herman ! 
First of all THANKS a bundle not only for your extensive reply, but also for your guidance ! And the links to Miles Comer's site. The Fixntldr.exe
on the floppy did not work, but Miles also mentions to use the windows disc for repair and at first i thought windows is going to re-install again ;( ...(it did not ask for my administrator-password now) 
I do not know yet whether it has succeeded... It takes a hell of a lot more time to have windows install a program, then it takes Ubuntu to have Jaunty installed ;) 
-
btw what IS your avatar ? is it an australian windmill to pump water up ? 
- 
anyway the situation now is that when my pc starts up it shows the familiar picture of elle mcpherson - if you want i send it to you gladly - and microsoft wants me to register now ! immediately !! but first I wanted to thank you -
what i think is that i have Grub installed in the second disc - with jaunty on it - i am now writing to you in firefox in jaunty - from ubuntu one can see the other discs - which is NOT possible under windows and i found boot.ini and changed it too what i think it should read - also to no avail. now the fine-tuning is for later i hope - 
what i also wanted to ask : is the Grub-page from you ? nice work !
i learned that when you use the grub-disk you can edit the commands - 
but first one has to learn to walk, before one can run right ? 
i hope till later OttO

---

### Post by Herman on 2009-04-19
> btw what IS your avatar ? is it an australian windmill to pump water up ? Yes, here in Australia where the climate is mostly dry and hot, windmills were and still are used for raising water from underground for watering livestock, and in the old days for water for steam engine boilers too. Windmills were and still are a great help to people living in the 'outback' or 'bush', and have come to symbolize man's ability to cope with a harsh environment by using his ingenuity. Not only cope, but flourish.
They have also become a symbol of the 'Outback', or the 'outback' way fo life, so in the town I live in we have moved one in from a station (ranch) and set it up in a park so tourists can see it. [URL="http://picasaweb.google.com/herman543/WirrillaWindmill#slideshow"]Wirrilla Windmill
[/URL] My avatar is made from a photo of that windmill, but I superimposed it over a different background. 
> when my pc starts up it shows the familiar picture of elle mcpherson - if you want i send it to you gladlyLOL, okay!
> what i also wanted to ask : is the Grub-page from you ? nice work !Thanks, I hope it's still easy enough for most people to be able to understand. I keep adding to it and it's getting a little bit complicated and cumbersome. If I had the chance to start again I would have split it up into several pages instead of trying to squeeze it all into one big long page.

Anyway, I have to go, I'm glad you're making good progress, bye for now...

---

### Post by Herman on 2009-04-20
> The Fixntldr.exe on the floppy did not work,Oh, okay. Now that I have had time to review Miles Comer's site I can see that a few changes have been made since last time I checked.
I have a CD from there which I downloaded a lot time ago and it's a great help for any Windows XP booting problems. It always boots Windows XP because it contains its own copies of the three vital Windows XP booting files, NTLDR, NTDetect.com and a generic version of boot.ini that will boot Windows XP in various partition numbers and hard disks.
That bypasses the MBR, boot sector, boot.ini, NTLDR and NTDetect.com, so it's a pretty effective boot disc. Then we can fix most Windows XP booting problems from within Windows XP itself. 
I didn't know about the 'Fixntlrd' being added, I haven't tried that out yet. The main thing I had in mind was to just help you to get Windows booted up to begin with. 
I have downloaded the new .iso file now myself and I'll take a look at it. I don't have a working Windows XP installation to test it on right now though. 

My WinGRUB Page contains a little information about boot.ini and how to edit it. I doubt if you'll need to do that, but you could take a look at it and check it. [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html").

Most of the time, Windows XP booting problems can be fixed with a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), and besides FIXBOOT and FIXMBR, there's even the command BOOTCFG /REBUILD command. That command is for automatically fixing a corrupted boot.ini file or making a brand new one if one doesn't already exist, so you don't have to edit boot.ini by hand at all, (unless you want to).

---

### Post by Herman on 2009-04-20
> i learned that when you use the grub-disk you can edit the commands - 
but first one has to learn to walk, before one can run right ? Yes, I encourage everyone to have fun with GRUB and to try out [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), it's fun using GRUB's command line interface and you can learn a lot about GRUB that way.

I also think that people should have fun editing their /boot/grub/menu.lst files in Ubuntu.  Customize and personalize your GRUB as much as you like. 
If you're scared at all, you should get a [Super Grub Disk]("http://www.supergrubdisk.org/"), then you will always be able to boot again even if you make a mistake.

Regards, Herman :)

---

### Post by king2007 on 2009-04-21
Hey Herman, quickly reading your posts ... I shall have a look at the windmill-photoos-link you posted - i AM still looking at the Elle McPherson picture ...... it's OKEH to look at but the PC has to proceed which she does not :( tomorrow - I only work four days a week - it is bedtime now here in Antwerp and still trying to fix the booting process .... until tomorrow !

---

### Post by king2007 on 2009-04-22
Hello Herman,
todays comic is a good one !
[http://comics.com/herman/2009-04-22/](http://comics.com/herman/2009-04-22/)
your probably have seen it already ! LOL
i don't know yet how to upload here or whether it is permitted ?
one is not allowed to send a personal message until after 75 posts.... :(
anyways, i went to the shop on the bike for half an hour and i bought myself acronis - true image and disc director for a lot of money ...
still not able to start windows xp !! - i am going to write a protestletter to bill gates - now i need not only to register immediately my version of windows xp,  but also a file is needed which is called : 'msfeedssync.exe' ? never heard of ! 
actually what i like in Ubuntu is that when you want to do something - listen to the radio for example with rythmbox next question is do you want to search for packages yes install them yes and voilà you can enjoy your radiostation of your choice - easy as cake ! now you try that in windows ... boehoehoe update follows soon ):P)

---

### Post by king2007 on 2009-04-23
Hello Herman, i felt it was going to take a very long time so as i told you i bought acronis on two discs..... now when you understand cylinders and sectors and how a disc is built, maybe one can find the time to figure out which values has to go into which squares and thus -doing so- build meticulously a disc without errors. i just want to boot xp that is all i wanted !
i noticed you mentioned recovery console and when i insert the disc one can wait to enter R for repair. then you can enter dos-commands. if you are familiar with these or key-in : help. what i did wednesday-afternoon was instead of enjoying the sun on my terrace key-in chkdsk /r which supposedly repairs bad sectors. i also dared after that long process to key-in fixboot ! which was accepted, so the bad sectors seemed to be repaired ; the boot fixed - then i even dared to key-in fixmbr but windows warned me that doing so would cause irrepairable damage to the bootsector..... disappointed in the evening already i shutdown the computer and started to watch a football-game, which i normally do not do. now last night or this morning at four o'clock i thought : why do i not re-install vista ultimate ? within one hour it was installed and working properly together with a multi-boot screen... i have not dared to start xp because i fear for more problems. i also hesitate to download today the official release of jaunty jackalope - what would you do ?
i enjoyed the Wirrilla Windmill-complete slideshow - very nice, Herman with blue skies all over. 
I also shall have a look at : quote
My WinGRUB Page contains a little information about boot.ini and how to edit it. I doubt if you'll need to do that, but you could take a look at it and check it. WinGRUB Page.
unquote and now i am trying to find your mail-address bye for now OttO

---

### Post by Herman on 2009-04-25
:) I like this one: [http://comics.com/herman/2009-04-16/](http://comics.com/herman/2009-04-16/)
and this one: [http://comics.com/herman/2009-04-07/](http://comics.com/herman/2009-04-07/)
and this one too: [http://comics.com/herman/2009-04-04/](http://comics.com/herman/2009-04-04/)

I imagine it's more polite to just send links in to Ubuntu Web Forums rather than an actual image file, especially when it's not something that's directly concerning Ubuntu. This way we don't use up so much resources in the server.
I don't thing there's anything wrong with sharing a good cartoon though, and having a laugh. :)
> i noticed you mentioned recovery console and when i insert the disc one can wait to enter R for repair. then you can enter dos-commands. if you are familiar with these or key-in : help. what i did wednesday-afternoon was instead of enjoying the sun on my terrace key-in chkdsk /r which supposedly repairs bad sectors. i also dared after that long process to key-in fixboot ! which was accepted, so the bad sectors seemed to be repaired ; the boot fixed - then i even dared to key-in fixmbr but windows warned me that doing so would cause irrepairable damage to the bootsector..... disappointed in the evening already i shutdown the computer and started to watch a football-game, which i normally do not do. Yes, CHKDSK /R is supposed to 'recover data from bad sectors',  and mark them as bad so the operating system won't use them again. CHKDSK can't actually 'fix' bad sectors, I don't think any software can. CHKDSK /R implies /F, so it's a more powerful command than just CHKDSK /F, and it takes a lot longer. I think the length of time it takes would be the only problem with it. Probably that's why some people prefer just the /F switch.
> now last night or this morning at four o'clock i thought : why do i not re-install vista ultimate ? within one hour it was installed and working properly together with a multi-boot screen... i have not dared to start xp because i fear for more problems. i also hesitate to download today the official release of jaunty jackalope - what would you do ?
Re-installing Windows Vista Ultimate might fix it, but that depends on whether the problem is in the boot loader or deeper inside the operating system. I only know CHKDSK, FIXBOOT, FIXMBR and the BOOTCFG /REBUILD commands. I have never heard of the file called 'msfeedssync.exe', I don't know what that one does.
I also don't know very much about proprietary software licensing and registration and all that stuff. 

I would download Ubuntu Jaunty Jackalope and rescue all my files out of Windows XP and use Ubunu Jaunty Jackalope instead. That would be a lot easier and better too.

Regards, Herman :)

---

### Post by king2007 on 2009-04-25
Thanks Herman ! for your replies - I certainly like the cartoons
especially the last one : 
[http://comics.com/herman/2009-04-04/](http://comics.com/herman/2009-04-04/)
have you seen these ? 
[http://www.creators.com/comics/bc.html?comicname=bc](http://www.creators.com/comics/bc.html?comicname=bc)
you can even take an rss-feed.
I am subscribed to the netscape.org page which also starts with comics - we NEED these ! daily ;)
so to return to the subject - not overloading the ubuntu-servers
i have to figure out how people stick to their "old" distributions
- i saw one here was using dapper drake which is from 
1st of June 2006 - like you said rescue the files from disc one and continue using jaunty jackalope - but then october comes around and installs "kold kalimero" ? over my jaunty - then what ? how do you keep your data photos videos separate ?

---

### Post by Herman on 2009-04-25
There are several different approaches we can use for updating to the latest Ubuntu.

**Upgrade**
One way is to just upgrade from Hardy Heron to Intrepid Ibex, say for example, and then upgrade to Jaunty Jackalope now that Jaunty Jackalope is released. 
That works very well for the majority of people who like to do things that way. 
We do see a few people who run into problems, I suspect that those problems are mainly caused by installing software in Ubuntu that didn't come from an official Ubuntu repository, but there could be other reasons why people might run into difficulties, just bad luck maybe, I'm not sure. Every time I tried it, everything worked perfectly, just like clockwork. Personally, I don't prefer that method of upgrading though.

**Fresh Install**
Another way to do things is to back up all of our data, and re-install fresh.
It's easy to make a back up of all our files and data in Ubuntu. Most of our settings are stored in files inside hidden folders in our /home/username directories. Refer to my [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm")  page for more details.
All we need to do is make a backup of our regular files, (which we should be doing at regular intervals anyway, as a matter of routine), and also whatever hidden files we want to keep.
When we re-install the newest Ubuntu, we just copy and paste our old files and settings into our /home/username directory. It's very simple, and it encourages people to make a backup and learn how to restore from one. We should all be making regular backups anyway, so it shouldn't be any extra work.

**Separate /home**
Some people like to have a separate partition for their /home directory, to avoid the need to make a backup and restore their files again. I don't believe in that approach myself, I think it leads to laziness about making backups and wastes hard disk space by forcing people to decide on rigid partition sizes. Several very good and wise people have debated with me on that subject, but I'm a stubborn and I won't change my opinion.
(Some people think my stubbornness is because I'm a taurus and I'm also born in the year of the bull in Chinese horoscope, if you believe in that kind of stuff. It could be my breeding too, or my upbringing - sorry everyone, it's just the way I am).

**Install beside** (dual Ubuntu)
The way I did things myself for a long time was to make a new installation beside the older installation and keep using the older Ubuntu. 
Then when I'm ready, I copy the files from the /home/username directory into the newer version of Ubuntu.
Later, when the next new Ubuntu is ready, or I'm ready for it, I would install the latest version over the top of the older, obsolete one that I don't use anymore.

**Files and Settings Transfer Wizard**
We can also use the files and settings transfer wizard in the Ubuntu 'Desktop' Live/Install CDs to do at installation time that if we want.

**Simple Backup**
Another way is with a pair of great programs we can install called 'Simple Backup Config', and 'Simple Backup Restore'. Those make it easy for people to transfer their files and settings from one Ubuntu to another.

**Separate Data Disk** - (if we multiple boot)
This is what I'm doing now.
In my main computer I have four x 160 GB hard disks. 
Two hard disks are for operating systems, although most people wouldn't need anywhere near that amount of space for operating systems. I'm just a little different from most people.
The operating systems without any data in them don't take up very much room, but I allow around 20 GB each anyway.
Hardy Heron is my main operating system since it's the 'LTS' release, (Long Term Support), so it is the most stable. I have allocated 40 GB to Hardy Heron.

Actually I haven't had any bad problems even with alpha versions of the newest Ubuntu versions that are still under development - I must be lucky or something. The real reason I still use Hardy Heron as my main OS is only because my favorite program, 'Kompozer', is not completely updated yet to keep up with all the changes in the most advanced Ubuntu releases.

I don't store very many files or data in the operating systems themselves. Two of my hard disks contain data partitions, and most of my files and data are stored in those hard disks and not in any operating system at all.
I can mount my data partitions from any operating system, whichever one I have booted at the time, and work on the same data from any operating system.

It's important not to store any files with the same file name in two different operating systems. I have to be careful if I copy any file into my laptop and go away somewhere and make additions or edits to that file. I have to remember to make sure to empty the laptop as soon as I get home, into my data drive and overwrite any files with the same name there. Otherwise I might add something to the other copy of the same file and 'fork' the file. If I do that then I have to slow down and work harder and copy the changes from one file into the other file first. Sometimes that can get quite confusing and complicated and I could end up losing some of my work. That's the hazard of multiple-booting, and of having more than one computer.
Since I have a few different computers now and some of them have several operating systems in them, it's important to have a data partition and make sure I don't have any duplicate files. So, I try to keep my operating systems empty except for my main operating system, and files I either don't care about, or files I need to take with me in my laptop when I'm going somewhere.

Sorry for the long post, but I hope it will help some people to see the various ways of doing things.

Regards, Herman :)

---

### Post by king2007 on 2009-05-02
Herman, I do not understand why you say : sorry for the 
long post ??
it is very clear and understandabel understandbly ?? 
euh to be understood well
one line from you i liked to copy : 
I'm just a little different from most people. 

I want to read again your post tomorrow because now it is already sunday the third of may half past midnight already and too much beer is kicking -in 
my wife is screaming for attention !!
until later my friend ! thanks for the post !! :P

---

