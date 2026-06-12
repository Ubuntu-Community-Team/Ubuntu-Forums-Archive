---
title: "Adding A New SSD, installing Ubuntu, keeping old data"
date: 2014-08-16
forum: Hardware
---

### Post by em3raldxiii on 2014-08-16
My scenario is a little unusual, so I'll lay it all out there, and hopefully some other folks who have done this can give me a few pointers & some advice.  Also, I am already backing all sensitive stuff up.

This computer started out *years ago* as a 32 bit machine running Ubuntu 11.04 32 bit or some crazy shenanigans like that.  Over the years, I have replaced a lot of the hardware, to the point that pretty much the only thing that is the same is the primary HD, chassis, and power supply.  Over the years with Ubuntu I've just updated it, uninstall some drivers, install some other ones, and so on.  Of course, I've also made quite a mess of everything as well ... I mean, I'm a tweaker, but I don't always record what I do, so you can imagine it's a mess.  It still works, boots, and operates alright, but (despite how I always recommend people just fix their current install), I am thinking a reinstall is warranted so that I am using 64-Bit, eh?  Oh yeah, and this house is 100% MS free, has been since 2006.

Great, so then I am cruising around some computer hardware websites and I decide that it's finally time to update to a SSD for my OS drive.  It hasn't arrived yet, but I figured I would take this opportunity to get some advice.  I searched through the forums, but I had a hard time nailing down exactly what I want to do ... please forgive me if this is a well-trodden subject; if it is, just do me a favour and fire me a link.

Okay, so you can probably guess what I'm getting at here, but my biggest anxiety has to do with boot flags and convincing the machine to install to, and then boot from, the new SSD (ADATA 128GB 6GB/s) as opposed to the original drive that's in the machine right now (WD 2TB Black conventional drive).

Here's what I am considering doing (this is not exhaustive):

[LIST=1]
[*]Renaming the directories in the /Home partition directory to (username).backup so that the new user accounts do not pick up the old config files. (Yes, my ~/ directory is its own EXT4 partition)
[*]Installing Ubuntu 14.04 64 bit onto the SSD with the same /home partition (750GB), and the same /mnt/multimedia partition (1TB), and repartitioning the old / directory to a new /mnt/[something] directory.
[*]The entire SSD would be the / directory, and I assume it's still best to stick with EXT4
[/LIST]

Do I need to manually change the BOOT flag on the old / partition?
Do I need to do anything special with my BIOS (it's a new MB, but I haven't had any shenanigans with EFI or Secureboot, even immediately after changing the MB).
Any advice about the STEAM directory?  When I installed Steam, I just went with default _everything_, and I am not 100% sure where all the data gets stored (I know, I am a terrible sysadmin)

Okay, that should be enough to get some feedback.  I really appreciate all the effort everyone always puts into these forums ... so thanks in advance for *any* advice y'all might have.

---

### Post by yancek on 2014-08-16
Using a boot flag or marking a partition as active is needed on windows only and is not necessary for any Linux distribution.
You would need to enter the BIOS after installing to the SSD to set it to first boot priority.
I don't use a separate /home partition but, I understand that you should have an option during the install to NOT format that partition or make any changes to it.
With your separate multimedia partition, you would just create a mount point for it in the /mnt or /media directory and create an entry in /etc/fstab.

---

### Post by oldfred on 2014-08-16
If only Linux I prefer to use gpt. And since you may further update system I might suggest creating both the efi partition (future UEFI) and an bios_grub (current BIOS boot) partition.

My system started in 2006 with multiple upgrades. Most recent was a 64GB SSD a couple of years ago. I created efi, bios_grub & two partitions, one is now 12.04 and the other 14.04. The 12.04 will probably not get overwritten until 16.04 if still using this system. I also keep several test installs on hard drives, so every drive is bootable, just in case. I now keep /home inside my / (root) and link folders from my data partitions into /home in every install, so whatever I boot has same Firefox links, Thunderbird email and all my other data, but user configuration may be different.

Not sure how games work. I think they may default to / or /home, but you can specify other locations.

---

### Post by em3raldxiii on 2014-08-16
@yancek and @oldfred Thanks for the input.  It sounds like it shouldn't be too painful, then.  I won't likely have a system quite as complex as Oldfred as I usually don't update to the latest release until it's been out for a couple of months or more.  During the install, I will definitely be doing it manually and just specifying which partition to be what (without formatting them unless necessary).  The other partitions (/mnt/whatever) will definitely have an entry in the /etc/fstab, that part I have no problem with.  But this brings me to another semi-related thing!  Let's say in my /mnt/multimedia partition, there's a ../ music folder wherein I place all my backed up .FLAC files.  So now User1, and User2 (etc) link their ~/music folders to the counterpoint on the /multimedia partition.  Now, how do I ensure that when User1 backs up a CD that User2 has full access to it? (read/write for tagging, etc)?  So far I just periodically chmod -R the folder so that each user can access the folder.  I am sure there is a much more intuitive way to do this, I've just been too lazy to figure it out.

@oldfred I was unaware of the bios_grub partition as a convention.  So let me just beat it to death so I fully understand.  On the SSD I would create 3 total partitions:  two small ones (I am sure there's a minimum size) for EFI and for bios_grub, and then the rest of the drive will be one big / partition.  As for the /home directory, I like having it on its own partition, and I like the idea of starting fresh with no links/favourites/bookmarks at all.  I find a complete purge of all that _cruft_ can make the machine almost *invigorating* to use.  And I get the best of both worlds, too, by just renaming the existing user directories to /home/user1.backup so I can harvest important stuff after the fact.

---

### Post by yancek on 2014-08-16
> Now, how do I ensure that when User1 backs up a CD that User2 has full access to it? (read/write for tagging, etc)?

Put these users in group and give the group rw permissions.  Set that group for the directory/partition.

---

### Post by oldfred on 2014-08-16
The bios_grub and efi partitions are only if gpt partitioned and you may only need efi if in the future you add a newer motherboard that is UEFI and want to try UEFI booting.

This is the partitioning I have on my SSD.

```
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  316MB   315MB   fat32                   boot
 2      316MB   317MB   1049kB                          bios_grub
 3      317MB   30.2GB  29.9GB  ext4         Precise
 4      30.2GB  60.0GB  29.9GB  ext4         TrustySSD

```

I do not have more than one user, but some that do have suggested these group type settings.
       Group Permissions - Morbius1
[http://ubuntuforums.org/showthread.php?t=2138476](http://ubuntuforums.org/showthread.php?t=2138476)

 Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)
See lucky's post on network based shares & setting permissions commands
[http://ubuntuforums.org/showthread.php?t=1498422](http://ubuntuforums.org/showthread.php?t=1498422)

---

### Post by em3raldxiii on 2014-08-17
Wow, you guys are awesome!  @oldfred that is one extremely thorough response!  I give you my word that I will go through every single link and do some serious reading.  You are very kind.  

@yancek:  Aha, yeah, see ... I knew it was going to be something quick and easy like that.  I'll be honest and say that I haven't fooled with groups much since around 2007 when I was fiddling with network access for my kids user accounts and whatnot.  If I remember right, I ended up messing something up (probably something very simple) and causing my wife's account to not allow access to _anything_.  I thought it was funny for about 5 minutes ... haha!

---

### Post by oldfred on 2014-08-17
You probably do not need more than one or links. 
Each explains the solutions, but in slightly different ways or perhaps a slightly different configuration. Sometimes that helps in understanding what you want which may not be exact copy of their instructions.
I tend to over explain or over post links, and some then think it is too complicated.

---

### Post by em3raldxiii on 2014-08-17
@oldfred:  I, for one, appreciate all the work you put in. But then, I like to thoroughly understand what I am doing.  I haven't gotten through all the links yet, but I'm definitely getting a better picture of what I want to do, and the best way to put it in play.  Once I get my SSD (it should be here in a few days), I'll be ready.  And then I will post here to let y'all know what I ended up doing.  I figure it might help someone else one day to see the whole process, from asking the questions to putting the answers into action.

---

### Post by em3raldxiii on 2014-08-29
Update:  i made a USB stick with Ubuntu 14.04 64 bit.  Booting off the stick works, but the mouse & keyboard do not work in that live session.  Bizarre.  I read somewhere in the bowels of the Internet that it may actually be a Kernel issue.  I have already tried enabling and disabling every possible setting for the USB devices in my BIOS (including IOMMU), but nothing seemed to help.  I then realized that there is a 14.04.1 version available now, so that version is downloading right now.  If it works, and I am able to boot/install to my new SSD, I will post here.

Edit:  I should also point out that enabling IOMMU in my BIOS also seems to have reduced some of the errors I was getting in my existing Ubuntu install.  AND my keyboard and mouse DO work in my existing Ubuntu install as well.

---

### Post by em3raldxiii on 2014-09-05
Update:  As I pointed out on another thread, I ended up turning off IOMMU in the BIOS and then enabling soft-iommu in the kernel command.  All of the problems have been eliminated.  It appears that my particular Gigabyte motherboard is prone to this particular issue.  Something about their IOMMU implementation.

---

