---
title: "two hdd with two operating sys help"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by jokira247 on 2009-07-26
hi all i have two hard drives one 500gb and one 160gb i want to connect them both and install ubuntu on the smaller one and vista on the larger one and each hdd will have three partitions one for operating system and two for data and i want to be able to read all the partitions that contains data in both operating systems 

so how to do that and how to partition for both systems on both hdd?

also it is my first time to use ubuntu and i only tried it before with windows xp using wubi and i had also a question when i installed it i chose to give it 10gb of space and i found that it took this space completely  when i check the space taken from the drive from xp so what is this space for as in windows the windows only takes the space it requires and the rest of the drive is free so what is space take in ubuntu for?

---

### Post by ajgreeny on 2009-07-26
> **jokira247 said:**
> hi all i have two hard drives one 500gb and one 160gb i want to connect them both and install ubuntu on the smaller one and vista on the larger one and each hdd will have three partitions one for operating system and two for data and i want to be able to read all the partitions that contains data in both operating systems 

so how to do that and how to partition for both systems on both hdd?

also it is my first time to use ubuntu and i only tried it before with windows xp using wubi and i had also a question when i installed it i chose to give it 10gb of space and i found that it took this space completely  when i check the space taken from the drive from xp so what is this space for as in windows the windows only takes the space it requires and the rest of the drive is free so what is space take in ubuntu for?
The shared partitions will need to be fat32 or preferably ntfs, as windows can not read a ext3 partition without third party drivers, and there used to be some doubts as to the safety of those, perhaps they are OK now, but I have no idea.

I suggest you make a 20GB ext3 / (root) partition for ubuntu, and not bother with a separate /home partition, which many favour, as you will be keeping your data on a separate partition which is ntfs.  Your /home, which will only contain the mostly hidden folders and files needed for configuration, can not be on ntfs, but needs a proper linux file system to support the required permissions of /home files and folders, hence keeping it on the root partition, for now at least.  The rest of the disk, less swap (see later) can be divided into the two data partitions (ntfs).  You will need to edit your /etc/fstab file to enable the mounting of the data partitions at boot time, but we can come to that later, and you will also need to ensure that all your applications producing docs, photos. music, etc etc, use these data partitions as storage, easily done when you first use them.

You can choose the size of these partitions, either at install time, or preferably, I think, make them first using the live CD's gparted (System > Administration > Partition Editor, which can make and format tyo ntfs for you.  Leave formatting the 20GB for root until you install or format to ext3 if you prefer to make it easier to locate when you are installing, which is what I do now when I install a system.  Don't forget to leave a small partition of perhaps 2GB as swap partition at the end of the drive.

I can't really help with the windows setup as I am too rusty on that now, and in the past when I did install it, it always went on the whole drive, no separate partitioning involved.

I hope this all makes sense.  It can be a bit difficult to put into a few sentences ones suggestions for a complicated partitioning job, but it may all become a lot clearer when you get to actually do it with gparted on the live CD.

Good luck!

---

### Post by merlinus on 2009-07-26
With 160G for linux, I strongly suggest a separate /home partition, where application configurations and setups, passwords, bookmarks, email and such live.  You could allocate some 5G for this, and then when reinstalling, or installing a newer version, would not lose this info without having to back it up.

And it is much easier to create this whilst installing than having to carve a partition later by shrinking another, and moving it there.

---

### Post by jokira247 on 2009-07-26
i have a question if i decided to make my space like this

160gb hdd

20gb root
10gb swap as i have 4gb ram and i know that swap must be double my ram
the rest home

500gb hdd
20 gb vista
rest ntfs storage for my files

will i be able to see the 500gb hdd partitions in ubuntu so that i could transfer some files from 160gb hdd to the 500gb hdd

also will i get a screen to chose from vista or ubuntu when booting or this wont work?

also which operating sys to install first vista or ubuntu?

---

### Post by ajgreeny on 2009-07-26
I personally tend to not bother re-using the configs in my /home when I update the system from distro to distro or even from version to version of ubuntu; I find it better to start again, though I accept that is different from many other people's ideas.

Certainly, if you prefer, make a separate /home and /(root).  As a new user it could be that you need to install more than once, as I did, because I broke my system a couple of times when I first started using ubuntu with v5.04, and needed to reinstall it.  Now I know more or less what I'm doing, I don't bother with a separate /home, but just backup regularly and then start again with 99% new configuration when I upgrade distro, just keeping a few of the config files and folders I definitely do need, eg /.mozilla and /.mozilla-thunderbird, /.openoffice, and one or two files I need.

I accept that I now know my way around the system so well that it is easy for me and may not be quite so easy for you, and as I sit here typing and think more about things, I suspect merlinus may be right; perhaps for you a separate /home may be a lot easier.  Perhaps I should have a complete rethink for my own system as well.  I can always just delete old configs I don't want to keep, or manually rename them so they are not used.

EDIT:
Just seen your question re swap.  With 4GB ram swap may not be needed at all, but certainly 10 GB will be overkill.  Use 4GB if you must, but 2GB would be my choice, unless you will be needing to hibernate a system with huge amounts of data still open, when it's just possible that 4GB will be better.

You will be able to see the windows partitions from ubuntu, but not the other way round, hence the need to put /data on an ntfs partition which windows will see.

Install windows first then ubuntu for ease, though it is possible to get grub back easily if you do it the other way.  Grub will offer you the option of which OS to boot to when you startup the computer.

---

### Post by redspider on 2009-07-26
"4 gigs of ram" unless u use the hibernate feature there is no need for u to need a swap partition on a faster rig. if its first dual boot pc, install to winblows first. grub should automaticaly detect it then when installing ubuntu. grub is the default bootloader (lets you chose which os to run)  DAMN! already stated. quick replys today. :P

---

### Post by merlinus on 2009-07-26
Depending upon how many windows apps, and their size, you will be installing, with all that space I would give 30G to vista.  Again, much easier to get it right the first time without having to carve out space later on from other partitions.

aj is completely correct re: /swap.  I use 1.4G with 4G RAM, and even that is probably overkill.

---

### Post by jokira247 on 2009-07-26
thanks to all of u mates i am beginning to love ubuntu before i use it because of this wonderful community

---

