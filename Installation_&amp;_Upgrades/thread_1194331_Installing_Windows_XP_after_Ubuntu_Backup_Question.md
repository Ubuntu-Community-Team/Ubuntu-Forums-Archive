---
title: "Installing Windows XP after Ubuntu Backup Question"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by 5nak3 on 2009-06-22
Hi all, 

I've been using Ubuntu solely on this PC for a while now, and I'm happy with it, although it must be said MS Office and a couple of games (soldat and quake live) keep forcing me to boot up my other PC.

As a result I would like to create a small 10gb partition for XP to reside on.

Now my problem is that I have ubuntu already installed, and I have many many settings and configurations set up as well as numerous programs, music files, pictures etc which I don't want to go through the hassle of reinstalling and configuring everything.

There are numerous guides which I've found on these forums and on the net that tell me how to resize Ubuntu to make space for XP, but none talk about the backing up of the Ubuntu partition.

My question therefore is two fold:

1) Is there any application that can essentially take a "picture" of the hard drive as it is, all the settings programs etc etc... back that up to another location DVD or zip file on an external hard drive and then restore it. Thereby allowing me to wipe ubuntu, install xp, and then install ubuntu again?

2) I am slightly confused about using gparted. If the above program does not exist, I want to resize and make space for XP. Obviously I'll back up the most important documents (my pictures, music and work documents), and then try the resizing.

So if I am not mistaken all I have to do is load the ubuntu live cd, resize/move the slider within gparted to create space for XP (making this new partition NTFS), but how do I ensure it goes in front of the ubuntu partition?

The guide I found:

[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)

Both show the resizing of the Ubuntu partition from the right hand side slider. This means that the NTFS partition will not be first and most likely will not be the C: partition for windows. Is there any way around this?

Any help would be greatly appreciated. Obviously I want the quickest, and most pain free method available as that would help matters greatly, but if there is another method which someone can advise I'm all ears. My biggest concern really is just the fact I do not want to fiddle with settings too much as I'll be spending enough time trying to get XP secure and running the way I liked with with my choice of programs. 

Many thanks!

---

### Post by anystupidname on 2009-06-22
TimeVault, HUBackup, Clonezilla, and many more...

---

### Post by 5nak3 on 2009-06-22
Hi there thank you very much for the prompt response, it seems out of the three you mentioned HUBackup is the one I'm more willing to use (partly due to the GUI)

But after finding a user guide for HUBackup
[http://www.ubuntugeek.com/hubackup-backup-application-for-ubuntu-home-users.html](http://www.ubuntugeek.com/hubackup-backup-application-for-ubuntu-home-users.html)

It seems to me (and please feel free to correct me if I am wrong) that HUBackup is primarily aimed at backing up the Home part of the disk and not necessarily the whole file system.

Ideally my first choice option would be to create a clone of my existing ubuntu install as it is. Wipe Ubuntu and install windows, finally partitioning the HDD and then restoring my Ubuntu clone.

While it seems that Clonezilla is capable of doing exactly what I want I am not comfortable with the interface.

I'll try and find some alternatives, or I may just backup with HUBackup and then wipe the HDD and start over, replacing the home directory with the HUBackup one.

---

### Post by anystupidname on 2009-06-22
Your evaluation is accurate. I'm not sure I understand why you do not like the Clonezilla interface. If you use it with/via lubi/unetbootin, things run smoothly. But, I'll make an alternative suggestion which I've used before and you might like: bubackup (which uses unetbootin if I remember correctly)

---

### Post by 5nak3 on 2009-06-22
I'm just on my way out so I'll keep this post short. It isn't so much that I do not like the interface of Clonezilla, but more the fact that I've never messed around with partitions before so I'd like to keep things as simple as possible to avoid any problems. 

Clonezilla, seems a bit out of my depth, but I'll look into it when I have some more time, and I'll also look at the bubackup you suggested a bit later.

Once again, I'd like to thank you very much for your help so far.

---

### Post by dstew on 2009-06-22
[Partimage]("http://www.psychocats.net/ubuntu/partimage") is another way.

---

### Post by 5nak3 on 2009-06-22
hmmm partimage with the step by step provided seems quite easy actually. I might just test out see how I get along with it, and if that fails I'll give bubackup a try.

---

### Post by Mark Phelps on 2009-06-23
There is also P.I.N.G (Partimage Is Not Ghost), a front-end to using partimage that comes in a bootable CD, which can be used to create image files of your complete installation, and later, by booting from that same CD, restore your installation from the files.

Only problem, though (and I don't know if it's native to partimage), is that it restores the entire partition to the state and size it was when you made the backup.

So, if you (1) do the backup, (2) shrink the partition, (3) install XP in the unallocated space, you won't be able to restore from the images because the new partition is too small.

However, if you shrink the partitions first (would recommend using the GParted Live CD from distrowatch.com to do this), and THEN to the backup, you can later restore those partitions using the boot CD and the backup.

---

### Post by anystupidname on 2009-06-23
> **5nak3 said:**
> hmmm partimage with the step by step provided seems quite easy actually. I might just test out see how I get along with it, and if that fails I'll give bubackup a try.

Um... Clonezilla USES partimage...

---

