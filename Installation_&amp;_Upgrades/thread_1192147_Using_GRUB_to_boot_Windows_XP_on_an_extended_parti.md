---
title: "Using GRUB to boot Windows XP on an extended partition"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by o2mcgovem on 2009-06-19
Hello, 

A weird turn of events means that I have a PC with Windows XP installed on an extended partition with no way to boot into it. When I start the computer, it does nothing. 

I was just wondering, could I install Ubuntu in another partition and then use the bootloader installed by it (grub?) to boot into Windows XP despite it being on an extended partition? 

It'd also mean that I'd be able to play with Ubuntu whilst still having the familiarity of XP to go back to :D

Thanks,
Michael.

---

### Post by merlinus on 2009-06-19
You can certainly give it a try, but I would doubt that xp will happily run from a logical partition.

---

### Post by o2mcgovem on 2009-06-19
Thanks for the quick reply! :)

Um, I know this is an Ubuntu forum but any ideas for solving my problem? Can GParted convert an extended partition to a primary one?

---

### Post by starcraft.man on 2009-06-19
I assume a weird turn of events is short for "night of binge drinking with IT friends" :P.

Anyway, I'm having a vague recollection of having dealt with someone in a similar situation. I think the answer is yes, so long as the XP partition isn't damaged or otherwise unreadable. Grub is pretty good at auto detecting. So go ahead and install and we shall see how it turns out. In any event, can't damage anything so long as your installing to separate partition.

Edit: No, not directly. You can't just push a button and transform an extended partition into a primary one. The easiest solution I can think of would be to create a primary partition of equal or just enough size to store the info and copy all the data from the extended to the new one. Then reinstall Ubuntu and grub will detect it (or just run the grub live disk). Make sure to delete the extended after, don't need two copies.

I still think Grub might surprise ya, works great in my experience.

and REMEMBER, BACK UP!!! We aren't responsible for data loss from gparted.

---

### Post by foxmulder881 on 2009-06-19
> **o2mcgovem said:**
> Thanks for the quick reply! :)

Um, I know this is an Ubuntu forum but any ideas for solving my problem? Can GParted convert an extended partition to a primary one?

Well one has to ask you, what the hell is XP doing on an extended partition in the first place?

Also, I'd suggest you reinstall everything and clean up your partition table for a fresh start. It'll solve all your problems.

---

### Post by o2mcgovem on 2009-06-19
Phew, you guys reply fast! (Not that I'm complaining, it's great :) )

Okay, I guess I should explain this "weird turn of events". I wanted to save you all the reading :p, unfortunately no booze or "IT friends" involved.

Earlier today, I wanted to re-install the copy of Windows XP on my desktop PC, but the hard disk I use for backups died the other week so instead I created a FAT32 partition (partition #2 for the sake of clarity) on the disk that Windows XP is installed on and copied over all important documents and pictures. Then, I installed XP to the other partition (partition #1). Everything went fine, I copied over all documents from partition #2 to partition #1 without a hitch.


Since I had no use for partition #2 now, I opened up GParted on a live CD, deleted it and extended partition #1. But now, Windows XP won't boot. When I boot into GParted, it shows the partition with Windows XP on as an extended partition. 



I'm guessing XP instaleld a bootloader to partition #2, which said to boot XP from partition #1. So, XP must be able to live happily on an extended partition since it put itself there.


foxmulder881, since I have no where to put 50GB of data I can't really re-install everything at the moment. At the end of the month when I get paid I can buy an external hard disk, but in the meantime people will want to use this desktop PC so I could do with figuring out a way to boot into XP, even if it's just temporary :)


Sorry for this overly long post, and thanks for all the support so far. :)

---

### Post by fuzzyworbles on 2009-06-19
this is sort of a lazy reply, but i remember that there are some grub commands that are good at faking out windows -- to make it believe that it's actually the first partition. 

.. google (or whatever) for how to use the **map** command in **grub**.

---

### Post by boof1988 on 2009-06-19
Just a waaaay wild guess here :)

You could maybe try [*Super GrUB Disk*](http://www.supergrubdisk.org/) to automatically fix it.  Though I don't know if it will work or not.  (Hopefully the Super GrUB Disk can fix it though)

One other option (that seemed to work for me) was to have an ntfs partition at the beginning of the drive (mine is only 128MB) and then the Windows XP installation used it for some files (boot maybe?).  If Super GrUB can't fix your boot problem, maybe (if you have space and if you don't already have one) you could put a ntfs partition at the beginning of the drive and see if that helps.

```

user@host:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006be67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          16      128488+   7  HPFS/NTFS   [COLOR="Red"]# Windows XP boot stuff (contents shown below) on this partition[/COLOR]
/dev/sda2              17          32      128520   83  Linux
/dev/sda3              33       60801   488126992+   5  Extended
/dev/sda5              33       51025   409601241   83  Linux
/dev/sda6           56765       58677    15366141   83  Linux
/dev/sda7           58678       60589    15358108+   7  HPFS/NTFS    [COLOR="Red"]# Windows XP installation on this partition[/COLOR]
/dev/sda8           60590       60801     1702858+  82  Linux swap / Solaris

```

Contents of /dev/sda1...

```

drwxrwxrwx 1 root root   4096 2009-06-10 15:11 .
drwxr-xr-x 4 root root   4096 2009-06-19 19:43 ..
-rwxrwxrwx 1 root root      0 2009-06-09 14:45 AUTOEXEC.BAT
-rwxrwxrwx 1 root root    211 2009-06-09 14:40 boot.ini
-rwxrwxrwx 1 root root      0 2009-06-09 14:45 CONFIG.SYS
-rwxrwxrwx 1 root root      0 2009-06-09 14:45 IO.SYS
-rwxrwxrwx 1 root root      0 2009-06-09 14:45 MSDOS.SYS
-rwxrwxrwx 1 root root  47564 2004-08-04 06:00 NTDETECT.COM
-rwxrwxrwx 1 root root 250048 2009-06-10 14:19 ntldr
drwxrwxrwx 1 root root   4096 2009-06-10 15:03 System Volume Information

```

References:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by merlinus on 2009-06-19
IIRC the map commands are to boot from other hdds, not other partitions, e.g.

map (hd0) (hd1)
map (hd1) (hd0)

---

### Post by foxmulder881 on 2009-06-19
What about fixing the XP master-boot-record (fixmbr, fixboot) and then reinstalling GRUB afterwards?

Would that work?

---

### Post by starcraft.man on 2009-06-19
> **o2mcgovem said:**
> Phew, you guys reply fast! (Not that I'm complaining, it's great :) )

Okay, I guess I should explain this "weird turn of events". I wanted to save you all the reading :p, unfortunately no booze or "IT friends" involved.

Earlier today, I wanted to re-install the copy of Windows XP on my desktop PC, but the hard disk I use for backups died the other week so instead I created a FAT32 partition (partition #2 for the sake of clarity) on the disk that Windows XP is installed on and copied over all important documents and pictures. Then, I installed XP to the other partition (partition #1). Everything went fine, I copied over all documents from partition #2 to partition #1 without a hitch.


Since I had no use for partition #2 now, I opened up GParted on a live CD, deleted it and extended partition #1. But now, Windows XP won't boot. When I boot into GParted, it shows the partition with Windows XP on as an extended partition. 



I'm guessing XP instaleld a bootloader to partition #2, which said to boot XP from partition #1. So, XP must be able to live happily on an extended partition since it put itself there.


foxmulder881, since I have no where to put 50GB of data I can't really re-install everything at the moment. At the end of the month when I get paid I can buy an external hard disk, but in the meantime people will want to use this desktop PC so I could do with figuring out a way to boot into XP, even if it's just temporary :)


Sorry for this overly long post, and thanks for all the support so far. :)

Ok, now I get it. How big is the drive in question? I assume it's more than the 50 already stored. 80 at least? I'm thinking of a way to reinstall and save all data, but you'd need at least a small buffer room above the required for the XP install.

---

### Post by o2mcgovem on 2009-06-19
Again, thanks for the swift replies.

> Ok, now I get it. How big is the drive in question? I assume it's more than the 50 already stored. 80 at least? I'm thinking of a way to reinstall and save all data, but you'd need at least a small buffer room above the required for the XP install.

Good guess, it's 80GB!

> What about fixing the XP master-boot-record (fixmbr, fixboot) and then reinstalling GRUB afterwards? Would that work? 	

I tried booting into the XP recovery console and using fixboot and fixmbr. It was the first thing I did actually, it didn't work :/

>  You could maybe try [*Super GrUB Disk*]("http://www.supergrubdisk.org/") to automatically fix it.  Though I don't know if it will work or not.  (Hopefully the Super GrUB Disk can fix it though)

I'm looking at the SGD thing now. Using this won't make the problem worse if it doesn't work, will it?


Thanks for the help thus far, much appreciated. :)

---

### Post by starcraft.man on 2009-06-19
Ok, so I want to clarify, the way you have your partitions configured is you have partition one the XP install with data 50GB is extended, and the rest is unused space? From the way you write, I assume you moved the free space to the extended partition. So, this is how I see you recovering data quickly and getting XP/Ubuntu working.

1. Boot gparted. Move the remaning 30 GB out of extended, and to free space and make it a primary drive. Then install XP as normally to this 30 GB primary partition. You'll have space left over.

2. Boot into XP (fresh install), move X amount of data over into new primary partition. Leave at least 1 GB or more free on the new primary. 

3. Boot into Live CD for Ubuntu. Then go to terminal and install the ubuntu-restricted-extras package (i.e. sudo aptitude install ubuntu-restricted-extras). Once done, mount the old hard drive (should be under places, It'll be 50GB) and delete the data that was copied over to the new partition. Unmount the partition.

4. Install gparted from terminal in the live CD (sudo aptitude install gparted). Open it with root, alt + F2 and type (gksudo gparted) then enter. Then resize the partition you just removed and freed data from and add the free space up toward the primary partition. Close gparted.

5. I assume you got about 25GB up to your primary, so repeat above step and mount both drives this time. Copy data up to primary new drive. Repeat delete and resize. Eventually it will all be up to the functioning primary. Sort files and make proper.

6. Leave around 20 GB or so on the extended partition, install Ubuntu to this and all will work gloriously.

I think those 6 steps should resolve your trouble. A bit involved, but I'm pretty sure it will work. Might take a bit of a while though depending on hardware. I give my usual warning, using gparted without a backup if these are vital data runs risks. In my experience however, I've rarely had trouble, unless it's the unforeseen like a power outage. That's my solution, it sounds right in my head and I just read it over, so I think it ought to work. If you got any questions before hand ask BEFORE making things permanent.

---

### Post by o2mcgovem on 2009-06-19
Starcraft.man, I had this idea myself but wasn't sure about going ahead because then there'd be two copies of XP on the same computer. Do you think there'll be a conflict at all?

Well, I say I had that idea but mine wasn't as fun cos it didn't involve booting into Ubuntu. :p

Also, I may need some help with step 6; normally I find it's pretty simple to dual boot Windows and Ubuntu, but the partitions are messed up and stuff on this computer.

Thanks for this, I really do appreciate all the effort you've gone to :)

---

### Post by starcraft.man on 2009-06-19
> **o2mcgovem said:**
> Starcraft.man, I had this idea myself but wasn't sure about going ahead because then there'd be two copies of XP on the same computer. Do you think there'll be a conflict at all?


No. Once the primary partition is created and you install XP to it, it will be the only partition that boots. The XP bootloader is pretty dumb in the sense that it isn't aware of anything except itself.

Now that I think of it, you can just go ahead and purge the Windows directory of the extended partition (the 50), I mean we won't be booting into it ever anyway. That will give you extra free space to move up to the primary.

> Well, I say I had that idea but mine wasn't as fun cos it didn't involve booting into Ubuntu. :p
I like that, in case of any issue, you can always log on here and get help.

> Also, I may need some help with step 6; normally I find it's pretty simple to dual boot Windows and Ubuntu, but the partitions are messed up and stuff on this computer.
I don't forsee much trouble. Once you transfer all the files you want to keep up to the primary drive, go back to gparted and format the extended. That will eliminate any trace of anything, you can even go so far as to delete the ntfs partition in the extended space. Then put in Ubuntu linux CD and it will be a simple install, the only partition will be XP with free space in an extended section for Ubuntu. Grub should give no trouble as the remaining XP install is perfectly clean.

> Thanks for this, I really do appreciate all the effort you've gone to :)

No problem, your very welcome.

Note: If your a bit unsure about anything else don't hesitate. And gparted has a nice site where they provide nice tuts with pictures on how everything works if you've any questions to that. I think I covered everything though.

---

### Post by o2mcgovem on 2009-06-19
Cool, well I'm gonna get cracking then. I'll post back with any updates. :)

---

### Post by Herman on 2009-06-20
Probably it's too late, but for future reference, it is possible to boot Windows XP in a logical partition using GRUB.

The worst problem is caused by Window's habit of deleting it's own bootloader files when it gets installed in a logical partition, it copies them to another Windows installation in a primary partition if one exists. If it has done that, then you need to get yourself a new copy of ntldr, NTDETECT.COM and boot.ini from somewhere. You can copy those files into the root of drive C: using Linux if you like, that's the easiest way.
You may need to edit the boot.ini file with the correct partition number. 

The other problem is, GRUB can't set the boot flag in a logical partition. Normally it uses the 'makeactive' command to set the boot flag. Since the 'makeactive' command can't set the boot flag in a logical, GRUB errors out and stops at that step of the boot-up.
We can easily set the boot flag with a partition editor instead though. You can use GParted to set a boot flag on the logical partition. Then edit /boot/grub/menu.lst to chainload Windows but without the makeactive command. It should boot. At least that worked for me when I tried it.

Regards, Herman.

---

### Post by o2mcgovem on 2009-06-20
> **Herman said:**
> The worst problem is caused by Window's habit of deleting it's own bootloader files when it gets installed in a logical partition, it copies them to another Windows installation in a primary partition if one exists. If it has done that, then you need to get yourself a new copy of ntldr, NTDETECT.COM and boot.ini from somewhere. You can copy those files into the root of drive C: using Linux if you like, that's the easiest way.
You may need to edit the boot.ini file with the correct partition number. 

Hello Herman, I did this part of your post before I came here. It didn't work. The second part was what I was looking for, really. 

Starcraft.man, your advice worked a treat. It took a while, but in the end it worked. I re-installed all programs and copied over music. It seems that along the way all of the family's pictures (Shared Pictures folder) went missing, but thankfully they're backed up in the cloud and Live Mesh is synching them back as we speak.

Also, I'm really liking this new version of Ubuntu, it seems really polished compared to the others I've tried. It's a shame I've bought into Microsoft too much, otherwise I could see myself using it.

---

### Post by starcraft.man on 2009-06-20
I'm glad your alright and got yourself all fixed up.

As to your latter part, ever thought of running a VM? VirtualBox is an interesting project you may want to look at. I use it on my linux production machine when I am in need of a quick windows XP program and don't want to reboot to boot windows. Running a VM can be a bit intensive, but long as your machine is something like Core 2 and beyond it's more than powerful.

Give it a look, pretty easy to set up and install. You will need another license of XP/Windows however. Some people (like me) own many extra copies and never had a problem with this.

Virtual box is in the repos, and has it's own site you can read over. Works on windows too for the other way if you want a VM to run Linux inside Windows.

Anyway, problem solved I believe, have fun.

---

### Post by o2mcgovem on 2009-06-20
> **starcraft.man said:**
> As to your latter part, ever thought of running a VM? VirtualBox is an interesting project you may want to look at. I use it on my linux production machine when I am in need of a quick windows XP program and don't want to reboot to boot windows. Running a VM can be a bit intensive, but long as your machine is something like Core 2 and beyond it's more than powerful.

We're too heavily invested in Microsoft for that; our TV runs Windows Media Center so we need a PC with Windows that can stream shows to the XBOX 360, we use Live Mesh to keep all of the household's PCs in sync and we practically live in Microsoft Office. I heard that the next version of Ubuntu will have Live Mesh-esque synchronisation in the box, so perhaps then.

Anyway, thanks for all the help, much appreciated. :D

---

### Post by ubseamus on 2009-07-23
> **Herman said:**
> you need to get yourself a new copy of ntldr, NTDETECT.COM and boot.ini from somewhere. You can copy those files into the root of drive C: 
 
This could be the solution to my problem:
 
[http://ubuntuforums.org/showthread.php?p=7531937](http://ubuntuforums.org/showthread.php?p=7531937)
 
 
But where can I get these files from. I booted up an old XP machine and searched for them but came up with nothing. Any Ideas?
 
Thanks

---

### Post by Herman on 2009-07-23
You should be able to find the three vital boot loader files in the root of the file system in just about any Windows XP operating system.

If you can't, you can go to the following website and download the .iso file to make yourself a special boot CD with it's own generic copy of boot.ini in it, plus NTLDR and NTdetect.com, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm")

You should be able to boot with that CD, from one of the ten entries in the generic boot.ini file. 
You can copy those files from the CD. 
You may want to edit the boot.ini file, and remove the unused entries at a later date.
If you have a Windows XP Installation CD, you can boot it into a [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), and  issue the command '*bootcfg /rebuild* ' command. That command is for automatically fixing your boot.ini file or making a brand new one if one doesn't already exist. See: [How to Use and Edit Boot.ini in Windows XP]("http://vlaurie.com/computers2/Articles/bootini.htm") - Computer Education.

NOTE: Please check by reading your Windows EULA to satisfy yourself that you're not breaking any laws by copying those files. Windows is a proprietary operating system and I'm not sure of the legal issues involved in repairing it. I do know that Microsoft themselves have a KB article telling people how to copy those three files to a floppy disc to make a rescue boot disc, but I'm not  a lawyer so I can't comment on legal issues. I think it will be alright. I prefer to stick with open source free software instead.

---

### Post by ubseamus on 2009-07-23
> **Herman said:**
> 
If you have a Windows XP Installation CD, you can boot it into a [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), and  issue the command '*bootcfg /rebuild* ' command. That command is for automatically fixing your boot.ini file or making a brand new one if one doesn't already exist.

Will this affect how grub works? I don't want windows to install it's own booting system.

---

### Post by Herman on 2009-07-23
You can safely install the Windows boot loader files and if you need to, you can also run BOOTCFG/REBUILD and even install Windows boot sector code to the Windows partition boot sector by running FIXBOOT from a [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") without affecting the bootability of any other operating system.

You should restrain yourself from running FIXMBR from your [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") though, because that will overwrite your GRUB code in your MBR and make your MBR point only to your Windows partition boot sector, and you'll only be able to boot Windows XP after that.
Don't worry about it too much though, if that happens you can easily just re-install GRUB to MBR with a few quick and easy commands and that will fix it again.

Regards, Herman :)

---

### Post by ubseamus on 2009-07-25
could not figure out how to fix the NTLDR problem on the existing installation, & I was getting tired of messing with it, so I repaired XP using the installation cd. I was unsure what would happen to GRUB after doing this, & as I feared, the machine booted windows directly [without grub] & I could not load Ubuntu.

Using the supergrub cd I burned from [http://supergrubdisk.org]("http://supergrubdisk.org/"), I was able to reinstall grub & after an edit to boot/grub/menu.list I can now load XP & Ubuntu as wished.

Thanks everybody, problem solved =D>

---

