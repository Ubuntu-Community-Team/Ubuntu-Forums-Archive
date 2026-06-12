---
title: "[SOLVED] no partitions detected"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by rudi009 on 2008-12-27
Hello people..
I'm new to ubuntu and and i'm not able to inatall ubuntu with the livw CD.here is the problem..
I've three partitions on my hard drive two are NTFS and one is FAT32.when i click install in ubutu it doesn't show any partition. I want to inatall ubuntu on fat32 10GB partition. please help..:confused:

---

### Post by Partyboi2 on 2008-12-27
Make sure that the partitions are unmounted before running the installer you can unmount then by going to Places>Computer and right click on the drive and choose to unmount..

---

### Post by rudi009 on 2008-12-27
hey buddy..that didn't help..installer shows one single disk.help....:confused:

---

### Post by rudi009 on 2008-12-27
somebody help please...:(:(

---

### Post by -kg- on 2008-12-27
> I've three partitions on my hard drive two are NTFS and one is FAT32.when i click install in ubutu it doesn't show any partition. I want to inatall ubuntu on fat32 10GB partition.

You're trying to install Ubuntu on a FAT32 partition?  I'm not sure that would work.

What method are you using for the partitioning section of the installation?  I'm not sure, but if you *can* install Ubuntu on a FAT32 partition, you would still need a Swap partition, and using the manual installation method you would need to flag the FAT32 partition as "/" so that the installer would know where to install.  You would also need to create the /swap partition and flag that as such.

Why would you want to install Ubuntu in a FAT partition?  There's bad fragmentation issues with FAT, and a host of other problems.  NTFS is little better.  And ext2/3 is a Unix/Linux file system; a file system that is native to it.

(Edit:) You know, there is a way to install Ubuntu on a Windows partition:

[WUBI]("https://wiki.ubuntu.com/WubiGuide")

I had forgotten about it until I thought about it a little.  You might want to check the above guide if you have good reason to want to install Ubuntu on a FAT partition.

---

### Post by tad1073 on 2008-12-27
> **-kg- said:**
> You're trying to install Ubuntu on a FAT32 partition?  I'm not sure that would work.

What method are you using for the partitioning section of the installation?  I'm not sure, but if you *can* install Ubuntu on a FAT32 partition, you would still need a Swap partition, and using the manual installation method you would need to flag the FAT32 partition as "/" so that the installer would know where to install.  You would also need to create the /swap partition and flag that as such.

Why would you want to install Ubuntu in a FAT partition?  There's bad fragmentation issues with FAT, and a host of other problems.  NTFS is little better.  And ext2/3 is a Unix/Linux file system; a file system that is native to it.
  ---------------- Now playing: [Incubus - Beware! Criminal]("http://www.foxytunes.com/artist/incubus/track/beware%21+criminal") via [FoxyTunes]("http://www.foxytunes.com/signatunes/")


Linux will not install on a fat32 or ntfs.

The partition has to be reformatted to ext2, ext3, or the file systems recognized by Linux.

---

### Post by Partyboi2 on 2008-12-27
Try using  pci=nomsi as a boot option. At the main menu press F6 and add ```
pci=nomsi
``` to the end of the line and press enter.
Is you hard drive a sata drive?

Edit: Also try```
 all_generic_ide
``` as a boot option as well.

---

### Post by -kg- on 2008-12-27
> Linux will not install on a fat32 or ntfs.

The partition has to be reformatted to ext2, ext3, or the file systems recognized by Linux.

Except with Wubi, right?  Or am I incorrect?  From the above link:

> Wubi is an officially supported Ubuntu installer for Windows users that can install and uninstall Ubuntu as any other Windows application, in a simple and safe way.

Also from the page is the following image:

[IMG]https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=wubi-123.png[/IMG]

Note in the image that the "Installation Drive" is C:  That would normally be the Windows partition.  That is why I assumed that, using Wubi, Ubuntu would be installed in a FAT (or NTFS) partition.

---

### Post by tad1073 on 2008-12-28
> **-kg- said:**
> Except with Wubi, right?  Or am I incorrect?

That is correct. I forgot about Wubi.

---

### Post by rudi009 on 2008-12-28
somebody help...:(
ok I tried  using commands on main menu and I've also formatted the partition to ext3 but still on installation when the partition manager starts it doesn't show any partitions. it just says use the entire disk.help:(

---

### Post by rudi009 on 2008-12-28
also windows is no longer showing that partition:(

---

### Post by Partyboi2 on 2008-12-28
> **rudi009 said:**
> also windows is no longer showing that partition:(
If you formatted that partition to ext3 windows will not be able to see it as windows cannot identify the partition type.

---

### Post by rudi009 on 2008-12-28
please help me in installing up ubuntu. :(

---

### Post by Partyboi2 on 2008-12-28
Try manually creating the paritions for the install first.
Boot the ubuntu live cd and choose to use ubuntu without installing. Then when you are at the Desktop open up  gparted (System>Admin>Partition Editor) Delete the 10 gig ext3 partition you made. Then make a new ext3 partition as well as a /swap partition
Your swap should be roughly around x2 times the amount of onboard ram, but don't use more then 3 gig towards /swap.  So if you have 512mb ram you will only need to make a 1 gig swap partition. 
To create a swap right click on unallocated space and choose "new" and adjust the size to the size you want then at "filesystem" change that to linux-swap.
To create the ext3 partition is the same process (unallocated>New>create size>Filesystem>ext3) Once you have made these 2 partitions take note of there partition name eg /dev/sda2, /dev/sda3 as you can use this to identify the parititons during the partitioning stage of the install.
Then click on the install icon on the desktop, when you get to the partitioning stage choose "manual" then  edit the ext3 parttion (dev/sda?) and make the mount point / then make sure that the swap (dev/sda?) is set as swap. Then proceed with the install.

---

### Post by rudi009 on 2008-12-28
gparted is not showing any partitions..:(:(

---

### Post by urban_ryoga on 2008-12-28
I'd like to say that I'm having the same exact problems that rudi009 is having although my situation is slightly different. In my situation I already have installed 8.04 and I am wanting to upgrade to 8.10. When using the upgrade option on an existing install by following instructions on the Ubuntu.com webpage I run into issues with my boot becoming fubar (I went back and forth on the IRC forums for about a day with no solution so I was forced to reinstall 8.04 on my / partition.

After downloading the 8.10 iso and burning to a disk, I attempted to use the live cd to install 8.10 to my / partition, however none of my existing partitions are detected. This is the same issue that rudi009 has, except I have a working install of ubuntu. This makes no sense to me as this is the first upgrade I've had so many issues with.

I have three existing partitions for my current installation:
an 8GB / partition
a 2GB swap partition
and a 150GB /home partition

let me know of any addition information I need to provide.

---

### Post by rudi009 on 2008-12-29
help needed urgently..I'm doomed
I admit I messes up  but now I really need help. Here is what I did..
in my windows partition i used "pq boot for windows" to boot from 10 gig partition  which didn't had anything to boot.so my computer didn't started as there wasno operating system in that partition. then  I installed windows in that partition and also installed partition magic there and again used "pq boot for windows" and told it to boot from earlier windows partition.but now I am not able to see both of my other two partitions- 70gig and 10 gig and the 70gig one contains world's most precisions data. I'didn't do anything with that partition but still I'm not able access that. worst part is that now when i use live cd it shows that partition but i'm not able to access anything in that which earlier i was able to. now the most important thing is HOW CAN I GET ACCESS TO MY 70 GIG NTFS PARTITION](*,)](*,)PLEASE HELP

---

### Post by urban_ryoga on 2008-12-30
> **rudi009 said:**
> help needed urgently..I'm doomed
I admit I messes up  but now I really need help. Here is what I did..
in my windows partition i used "pq boot for windows" to boot from 10 gig partition  which didn't had anything to boot.so my computer didn't started as there wasno operating system in that partition. then  I installed windows in that partition and also installed partition magic there and again used "pq boot for windows" and told it to boot from earlier windows partition.but now I am not able to see both of my other two partitions- 70gig and 10 gig and the 70gig one contains world's most precisions data. I'didn't do anything with that partition but still I'm not able access that. worst part is that now when i use live cd it shows that partition but i'm not able to access anything in that which earlier i was able to. now the most important thing is HOW CAN I GET ACCESS TO MY 70 GIG NTFS PARTITION](*,)](*,)PLEASE HELP

dude... whatever you are doing stop... It is obvious that there is a problem viewing partitions on some computers with the 8.10 live cd. Messing up your windows boot is not good and the only way I know how to restore that boot is to reinstall. If you are unable to view the partitions with 8.10, please pick up 8.04 and use that live cd to backup your data onto an external hdd or even better if you have a second internal hdd you aren't using.

For all  of your basic installation, dual booting, and backup needs, please check [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index) . Again if it doesn't work for the 8.10 live cd use 8.04 as i've had no issues with it. The actual issue about 8.10 not seeing partitions is not as big of a problem as you think it is and I'm afraid you have done things to ruin your windows partiton. I can provide little help on that.

---

### Post by plarq on 2008-12-31
I just install 8.04.1 instead...
Installation complete.

---

