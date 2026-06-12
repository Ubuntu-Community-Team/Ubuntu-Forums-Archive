---
title: "Hard drive troubles!"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by Mathias-K on 2006-01-20
I've ran into a lot of blind ends on my Linux journey, but this has to be the biggest one yet.. 

I had some problems with my Kubuntu 5.10 install on my Linux harddisk. It would not boot because of some kdestartupconfig error, so i made a new Kubuntu install, and it worked out until i wanted some gaming, so i decided to install Windows XP Home Edition on it to make it a viable gaming rig, like this:

hda1 = Kubuntu 5.10 (errored)
hda2 = Edubuntu 6.04 F3
hda3 = Kubuntu 6.04 F3
hda5 = FAT32 trashheap partition
hda7 = Windows XP Home
hda8 = Kubuntu 5.10 (rescue install)

But like revenge from the gods above, the Windows installer somehow fails (it's a genuine CD that has never failed before), and when it has rebooted and should enter the graphical part of the installation, absolutely nothing happens. There is a black screen with a white underscore, and nothing is loading or working.

The real problem = i have some quite important files for school on my FAT32 trashheap partition :(

I have tried booting from a Kubuntu Live CD, and when i enter kcontrol and looks for disks and partitions, i can see that the files seem to be there, but i cannot enable them. It gives me an error that leads me to believe that i have somehow trashed the boot loader or something..

Also, if i try to install a new partition, the breezy (or dapper for that matter) installation can't edit the partition table manually. The only option it suggests is to start from scratch and format all my homework, which would be kinda bad..

Is there anyway that i can pull out my data from the partitions, especially the FAT32 one?:confused: I really hope that you can help me out on this stupidity.. 

Thanks in advance,
Mathias

---

### Post by morphodone on 2006-01-20
Yes, you can boot from a live cd - partition and copy files

there are several - knoppix, simplymepis, slax, etc...

just boot the live cd and copy files to another place like
a usb key or burn a cd if you have two cd drives

you can run slax in ram and burn a cd if you only have one cd drom

hope that helps

---

### Post by wrtrdood on 2006-01-20
And, BTW, I fairly certain that Windows MUST be the first partition of the drive and that's why it did what you describe.  As a result, it probably corrupted your partition table which may be why you're having trouble.  Unless you created a copy of the partition listing, you may be out of luck.  That listing (fdisk -l) gives you the starting and ending blocks of the partitions.  I'd try the livecd approach and try mounting each one to a temporary mount point then doing as morphodone suggests.  

How? 

mkdir /tmp/hd
mount /dev/hda1 /tmp/hd

---

