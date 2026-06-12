---
title: "shared partition XP/Ubuntu &quot;home&quot;-&quot;my docs&quot;"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by Orion2000za on 2006-01-30
Here is what I am planning to do and I need some help;
I want to run both XP and Kubuntu on a PC, this for work reasons (too much of my work involves Windows for me to be able to just kill it).
that is not a problem as such, install XP first and then Kubuntu, already tried.

BUT what I would love to have is like 3 partitions, 2 for OS (XP and Kubuntu) and the main part of the disk an ntfs partitions where I can put all userdata, be they "windows" or "linux". So My Documents would reside on this D: (from windows point of view) and /home would reside on this mount from Kubuntu's point of view.

Now here is where I ask for help cause otherwise I can see days and days go by with frequent reinstallations...

Orion

---

### Post by alamba on 2006-01-30
Make sure the 3rd partition is Fat32 and not NTFS. Write support for NTFS in linux is'nt completely matured yet.

Akshay

---

### Post by g3r41d on 2006-01-30
Yeap.. do not use NTFS as your third partition. Use FAT32 instead to allow reading and writing. And to access read and write of the partition check this link

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by mcduck on 2006-01-30
/home must be on a linux file system like Ext3 or ReiserFS. FAT doesn't support linux file permissions and ownership. And writing to NTFS is not supported. So you can't use same partition as home for both Win and Linux.

But you can make a FAT partition to transfer files between Windows and Linux, and you can even mount that to some folder inside your /home directory if you want.

---

### Post by Orion2000za on 2006-01-30
Problem with FAT32 is that it has a cap on size of files and I sometimes edit dvd-videos.... 
I see the thread gives the basics at least though I think you can mount ntfs as rw - but how do I make it /home ?

---

### Post by Orion2000za on 2006-01-30
Sorry, I saw "mcduck"s reply only now. OK /home has to be linux I can see why and a mount/link to can be done from /home. 

But I know I have seen ways to mount ntfs rw (stubborn...) and that is very much the preferred way to go if possible

---

### Post by pelle.k on 2006-01-30
You can't and shouldnt mount it as /home, as mcduck pointed out. What you can do is make a folder inside your /home like /home/ntfs and mount a ntfs partition to that folder.
You will have to make an entry in /etc/fstab wich points to that folder, and it will get mounted everytime you start up ubuntu.

I think ntfs rw support must be turned on when compiling the kernel, maybe theres a module for it?
Another way to mount a nfts partition rw, is to use captive ntfs, wich is a way to use native windows ntfs device drivers in linux. But be sure to back stuff up if you chose to use it.

Anyway, this guide can show you how to add partitions to fstab. Remeber where your partition is at (/dev/hda3 or whatever).
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by Orion2000za on 2006-01-31
OK, I decided to go ahead and tinker a bit by installing Kubuntu first on the remaining space of the disk and then see if I can mount the XP ntfs part and in what ways. Thinking I could then do the whole "3 partitions part" later using an external usb harddisk for backup.

Ran into trouble on installation, at the partitioning. The computer has a 50 Mb "recover" partition and then a 30 GB main partition. Of that some 14 GB is free. Now the installer tells me that I can resise ide1 (the 50 Mb) and then use ide2... and then suggests a MINIMUM size for the Kubuntu of 14 Gb and Max of 30 GB - in other words it wants to take over the whole partition. 

How can I change these settings, I can't figure it out from the installer.

Orion

---

### Post by pelle.k on 2006-02-05
Do "manually edit partition table" or whatever that  alternative is called during install. I always do. Resize whatever you want, then create three partitions with mount points "/","/home", and tha last with filesystem "swap". I usually go for sizes /home (whatever size) GB, / 5 GB, and swap 1 GB.

---

### Post by MadMan2k on 2006-02-05
make the exchange partiton ext3
[http://www.madman2k.net/?module=article&id=19](http://www.madman2k.net/?module=article&id=19)

or wait until ntfs write support is in the kernel. (yes it already works)

---

### Post by Orion2000za on 2006-02-06
Problem is the "manual edition"-thing doesn´t seem to work or I can't figure it out. I have tried to select an existing partition in order to change/resize it but all I get is the option of taking over the whole partition. What keys or commands is one supposed to use to resize?

Orion

---

### Post by pelle.k on 2006-02-06
well, as far as i can remeber, you get like 3 alternatives:
use entire hd, use free space on hd, manually edit partition table.

choose the last one, then you will have to choose which hd (hda, hdb, or in my case sda or sdb). After that you will se a list over partitions already on the drive.
There will be signs besides them, depending on the actions that will be performed when you are done setting up partition table (there might even be a help option which explains the meaning of the signs). you will also see where they will be  mounted at (like /home etc.)
If you click a partition you will be presented with a list of options. This is where, amongst other things, you can resize it if you click the size option.

Is this clear/accurate enough?

---

### Post by orangedoor on 2006-02-06
As for your "My Documents" folder. I had issues with permissions on mine that has to do with "system" files from Windows. I resolved it by running > attrib /s /d -r -h -a -s in a command prompt on my "My Documents" directory.

I also disabled thumbnail caching in folder options in windows, so hopefully I dont' have the problem again. (The problem is not being able to create folders in linux within certain folders that contained some of those "system" files).

It was a FAT32 partition and nothing I put in fstab could resolve it... I think I'll start a new thread somewhere about it, maybe there's a better solution.

---

### Post by Orion2000za on 2006-02-07
Tjena Pelle,
thanks for the help but no luck this far. All I get (I can't click since my mouse does not come alive during install) in manual edit is the choice to use the full partition. Since I can't click I follow instructions and try Space (nada happens) or Enter - that just tells me that the changes will be written to disk, in my case meaning the full 30 Gb will be reformatted. 

Is there another Keyboard key I should use to get the "resize" etc. choices??

---

### Post by pelle.k on 2006-02-07
Tjena Orion. Så du är svensk alltså :)

I tell you what, take a look at this guide: [http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2)
You should recognize the first screenshot, and choose a harddrive in the second. Since you already have partitions on your drive you shold now see something like in screenshot 5 (your disk, with existing partitions underneath)
Navigate to the partition you wish to shrink (using the arrowkeys), and click it using return/enter key. You will then have some alternatives - use them to your liking. (change the size etc.)
When your sone, select "done modifying partition" or something like that. you will now be back at screenshot 5, and there should by now be free space available.
Clicking the free space will let you create a new partition. Create 3 partitions, one with mount point / (make it 5 or 10 gb), /home (choose a size), and a swap partition (no mount point, just select file system "swap")

And by the way... The mouse isn't activated until installation is complete. Everyone including me is using arrowkeys, tab, space, escape, and return/enter to navigate during the entire installation.

Please come back and tell us if you succeeded...

---

### Post by Orion2000za on 2006-02-07
Tjena Pelle, jepp men Örjan funkar inte så bra utanför Sverige därav Orion. 

I have found another guide and have now managed to try the manual partition but I end up with the same scenario as the guided partition; the partitioner refuses to use less than all unused space as minimum and suggests the entire disk.

I guess I am going to have to give and go at it the hard way; backup all data, reinstall XP and then fdisk the whole partition into separate partitions. Then install Kubuntu and also create a mutual data-partition for both OS while I am at it.

Given the time that will remove from productive time though I don't see it happening during February.

Orion

---

### Post by pelle.k on 2006-02-07
OK... That kinda sucks :/ But anyway - a clean install of xp isn't all bad. I find i have to do it quite often to keep it functional.
Good luck with that, and i hope you will be back. Ubuntu is definitly worth it.

[edit] I just thought of something. Why dont you just download kanotix, run qtparted and shrink the ntfs-partition, then boot up your breezy install cd. Worth a try anyway...[/edit]

---

