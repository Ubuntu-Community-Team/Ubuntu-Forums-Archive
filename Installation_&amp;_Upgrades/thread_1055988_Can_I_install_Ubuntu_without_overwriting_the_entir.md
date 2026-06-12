---
title: "Can I install Ubuntu without overwriting the entire HD?"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by funky_uncle on 2009-01-31
My Mint system sort of crashed so I'm going to install Ubuntu. The LiveCD works fine and I can find my photos and music on the HD, but since
a) I can't back them up on CDs since the LiveCD has to stay in the drive, and
b) it's too much to make backups of everything anyway,
I hope I can copy these files to another, safe location on the HD and install Ubuntu without overwriting them.

---

### Post by boof1988 on 2009-01-31
> **funky_uncle said:**
> My Mint system sort of crashed so I'm going to install Ubuntu. The LiveCD works fine and I can find my photos and music on the HD, but since
a) I can't back them up on CDs since the LiveCD has to stay in the drive, and
b) it's too much to make backups of everything anyway,
I hope I can copy these files to another, safe location on the HD and install Ubuntu without overwriting them.

There are several options probably, but one option (if you have a working computer available) that I know of:

[LIST=1]
[*]Download [GPartEd LiveCD](http://gparted.sourceforge.net/livecd.php)
[*]Burn GPartEd LiveCD
[*]Put GPartEd LiveCD in target machine and boot it
[*]Choose "To RAM..." option on GPartEd boot menu (see screen shot)
[*]Remove GPartEd LiveCD after system loads
[*]Use the terminal to copy important files to blank CD/DVD
[*]Partition HDD (if desired) while using GPartEd LiveCD
[*]Keep fingers crossed
[*]Install OS of choice
[/LIST]

Hope this helps a bit.

---

### Post by balaknair on 2009-01-31
The GParted partition tool is already included on the LiveCD, and you can use it to resize one of the existing partitions to create space for a new partition. Once the new partition has been created, mount the partitions(the old partition as well as the new one), copy the files you want to save to the new one and then unmount all partitions. You can then proceed with the install, using the 'Manual partition' option when you get to the create partitions stage. Just make sure you select your old partition to install Ubuntu to, and leave the old partition untouched. After installing Ubuntu, you can use the new partition to store stuff on, or you can delete it after copying the files you want to save to the new install and expand your install partition to use the freed space(using GParted on the LiveCD).

---

### Post by funky_uncle on 2009-01-31
> **balaknair said:**
> The GParted partition tool is already included on the LiveCD, and you can use it to resize one of the existing partitions to create space for a new partition. Once the new partition has been created, mount the partitions(the old partition as well as the new one), copy the files you want to save to the new one and then unmount all partitions. You can then proceed with the install, using the 'Manual partition' option when you get to the create partitions stage. Just make sure you select your old partition to install Ubuntu to, and leave the old partition untouched. After installing Ubuntu, you can use the new partition to store stuff on, or you can delete it after copying the files you want to save to the new install and expand your install partition to use the freed space(using GParted on the LiveCD).Ah, exactly the kind of answer I was hoping for :)

But just so that I can learn a little about how this stuff works, why is it that I must unmount the partitions? Is mounting a partition sort of like plugging in a memory stick (Ubuntu doesn't see it until it's mounted)?

Would it be wise to have several partitions in any case, like if I want to try different distros later?

---

### Post by balaknair on 2009-01-31
I just noticed a small typo in my previous post(*Just make sure you select your old partition to install Ubuntu to, and leave the old partition untouched.* Make that leave the new partition untouched).

> **funky_uncle said:**
> Ah, exactly the kind of answer I was hoping for :)

But just so that I can learn a little about how this stuff works, why is it that I must unmount the partitions? 

I'll try to answer your questions as best as I can(based on my very limited understanding)

Mounting or unmounting partitions to make partition table changes: 
The OS uses a list of partitions and files to know where stuff is on your hard drive. Normally this contains only the partitions which have been mounted. When you mount a partition it gets added to this list. The OS basically reads this information as a long string of numbers telling it where on the disk a partition or file resides, sort of like geographic co-ordinates. Mounting basically tells the OS where in the directory tree the files should appear(usually something like "/media/PARTITION_NAME").
Since the OS needs this list to run smoothly(to know where all the critical files it needs are), editing partitions while it is mounted and being used by the OS can be disastrous. So it locks down the partition tables of all mounted partitions- while the OS is reading them, no one else is allowed to change their basic attributes. This is why you need to unmount a partition to make changes to it.


> Is mounting a partition sort of like plugging in a memory stick (Ubuntu doesn't see it until it's mounted)?

Pretty much. The OS kernel initially detects the hardware/firmware of an unmounted device but not the filesystem or data on it. It knows this is a data storage device, but it doesn't read the data till the disk is mounted. When the drive is mounted, the OS reads the partition tables(contained in the first few bytes of the drive, and describes the contents of the drive sort of like a table of contents in a book) to know what is on the drive and displays it.


> Would it be wise to have several partitions in any case, like if I want to try different distros later?

If you want to try different distros, it's probably better to leave sufficient free space rather than extra partitions. This way you can use the free space to either make new partitions or to expand adjacent partitions into the space should you need more space. Besides the default filesystem another distro or version uses might not be the same as what your current distro uses, leading to difficulties in booting. For example, Ubuntu 8.10 Intrepid Ibex uses a modified ext3 file system that uses 256 byte inodes(previous versions of Ubuntu and other distros use 128 byte inodes), and some older kernels cannot read such partitions. The advantages of larger inodes are that it can improve disk performance and reliability and is future-compatible with the ext4 filesystem(available with the 2.6.28 kernel in Ubuntu 9.04 Jaunty Jackalope). The disadvantage is it sacrifices backwards compatibility.

You can also have a separate /home partition, so that if you reinstall or upgrade Ubuntu, you won't lose your personal settings and data(like what happened just now with your Mint install).
An excellent guide on how to plan partitions is available here
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)


Hope you find this info helpful.

---

### Post by funky_uncle on 2009-01-31
> **balaknair said:**
> Hope you find this info helpful.It really is!

So what I gather from your posts and the link you gave me, when I (re)install Ubuntu I should create a separate partition for /home, right? Which will make it easier to (re)install distros later. When I look at /home in Nautilus it appears that that's where all my programs are installed as well (my disk has only one partition). Does that mean that I won't have to reinstall them when I install a new distro?

Sorry for asking all these questions, but I gotta learn it somewhere...

---

### Post by balaknair on 2009-01-31
> **funky_uncle said:**
> It really is!

So what I gather from your posts and the link you gave me, when I (re)install Ubuntu I should create a separate partition for /home, right? Which will make it easier to (re)install distros later. 

A typical Ubuntu install requires a minimum of 5 GB. A root (/) partition of 5 to 15 GB is usually more than sufficient for the '/' partition. If you have more than 30 GB on your hard drive for Ubuntu it's a good idea to set up a separate /home partition.

> When I look at /home in Nautilus it appears that that's where all my programs are installed as well (my disk has only one partition). Does that mean that I won't have to reinstall them when I install a new distro?

Sorry for asking all these questions, but I gotta learn it somewhere...

The installed programs are actually in /usr(almost all installed files for an app will be in /usr/bin/ /usr/lib/ and  /usr/share/ )and not in your /home folder. /usr/bin is where the executable file resides (like firefox.exe in C:\Program Files in Windows, you will have an executable firefox file in /usr/bin/ ), and other stuff like libraries for each app will be in /usr/lib/ , data which needs to be accessed by other apps to interact with each other will be in /usr/share/ and so on.
What you see in /home are the individual application settings for each user. Like the Firefox settings, addons, bookmarks, history, cookies, saved form data, and your email (Evolution or Thunderbird) configured accounts, settings, saved email messages etc. The /usr folder is a system folder, and normal users do not have permission to make changes to it(so to install an app you need admin privileges and have to use sudo. Changes made here affect all users on the system. But in your /home folder, you have full read-write privileges, and so your personal settings can be stored here, and if you accidentally mess something up other users on your computer will not be affected.
eg: To install or update Firefox, you need to run as root(or use sudo), but to install or update addons for Firefox, you can do it as a regular user, since the changes are made inside your /home folder. 

So if you preserve your /home folder, the personal settings for each app will be preserved, but you will have to reinstall all apps, libraries and codecs that are not part of the default install. Once installed they will behave like the apps on your previous install used to. If you want to recreate the installed apps on your current installation when you do a reinstall, you can try the steps given here
[How to Setup Ubuntu for Reinstalling your applications without losing your data]("http://mybrainrunslinux.com/node/2")

---

### Post by funky_uncle on 2009-01-31
Ah, and it just got a little more complicated :/

I'm trying to resize my partition to make space for a new one. Problem is it's a little too small - not enough room to copy the data from the old one. And I don't have permissions to delete anything from old one either.

It would work if my Mint installation would boot, of course, but it doesn't. Am I screwed?

---

### Post by balaknair on 2009-02-01
1) You can compress the stuff you want to save to fit into the available space(select the files you want>right click--> 'create archive'--> select location-> set the target location as your new partition).

2) Try using a USB external hard drive or a flash card/memory stick to get some extra space.

3) Back up files to a shared network folder on another computer or do an online backup.

4) To delete files from the old one: I think you can delete the files on your old partition if you use root(admin) privileges. To open the file browser(nautilus) with root privileges, press alt+F2--> type *gksudo nautilus*--> browse to the old partition and delete unwanted files.


FIXING MINT:
What error are you getting when starting Mint?
A boot failure could be just a GRUB error or a partition table error. In most cases, these can be fixed with the Live CD.
If the OS itself is borked, then you would have to reinstall, but this is usually rare in Linux systems(at least in my experience).

---

### Post by funky_uncle on 2009-02-04
Yeah, I forgot that I could use a USB stick, I guess that's why I shouldn't be doing these things at 4 AM.

Anyway, to make room enough on my disk I deleted everything but /home and began resizing the partion. GParted is working right now, taking a looong time... (should I be worried?)

When it's done, I plan to copy /home from my old to my new partition and delete the old partition, then I'll try to install Ubuntu - if I remember correctly, the installation will ask me how I want to partition the HD, and I'll tell it to make a 15GB partition for the Ubuntu installation.

Sound like a plan?

Noobly yours,
funky.

---

### Post by funky_uncle on 2009-02-04
> **balaknair said:**
> FIXING MINT:
What error are you getting when starting Mint?I think the last thing I did was to update some drivers for my nVidia card. Trying to boot, I'm only told the monitor or graphics card or something isn't supported. I could probaly fix it in some other way other than reinstalling Linux entirely, but I was looking for an excuse to try Ubuntu again.

---

### Post by funky_uncle on 2009-02-04
nvm

---

### Post by funky_uncle on 2009-02-04
When typing ```
sudo cp /old/etc/fstab /old/etc/fstab_backup
```(following the instructions to the dot),
I get ```
cp: cannot stat `/old/etc/fstab': No such file or directory

```and I have no idea where to go from there.

---

### Post by balaknair on 2009-02-04
Hi.
I'm in New Zealand right now for exams, will be stuck here with no regular internet access for a while(till the 17th at any rate). I'm typing this from a kiosk at the airport(no free wifi :( ). I'm terribly sorry to leave you hanging like this, and I really hope someone else will be able to help you for now.
Wish ya luck.
Signing off for now(only have 2 minutes left).
All the best.

---

### Post by funky_uncle on 2009-02-04
Thanks for you help, but I ended up having to do a clean install anyway.

---

