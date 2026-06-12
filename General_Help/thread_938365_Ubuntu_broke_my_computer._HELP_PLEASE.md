---
title: "Ubuntu broke my computer. HELP PLEASE"
date: 2008-10-04
forum: General Help
---

### Post by jeremytodd1 on 2008-10-04
So I had Ubuntu running on my computer through a CD, and then I tried doing the install using the CD. Everything was going fine in the installation until I got an error that said:

**Failed to create a file system**
The ext3 file creation system in partition #1
of SC(number that I can't remember) (0.0.0)(sda) failed.

Then the only option I could push was "OK." When I pushed that it started the computer up again. But then I get an error that says:

Master Boot Record Error
Press a key

That error is on a black screen and the text is in white. When I push a key it just says the "Master Boot Record Error press a key" thing all over again each and every time I push a key.

How do I fix this?

---

### Post by Prospero2006 on 2008-10-04
> **jeremytodd1 said:**
> So I had Ubuntu running on my computer through a CD, and then I tried doing the install using the CD. Everything was going fine in the installation until I got an error that said:

**Failed to create a file system**
The ext3 file creation system in partition #1
of SC(number that I can't remember) (0.0.0)(sda) failed.

Then the only option I could push was "OK." When I pushed that it started the computer up again. But then I get an error that says:

Master Boot Record Error
Press a key

That error is on a black screen and the text is in white. When I push a key it just says the "Master Boot Record Error press a key" thing all over again each and every time I push a key.

How do I fix this?

Ok, here is what happened:

The installation process completely formatted your hard drive.
Then, it tried to install an ext3 filesystem and failed.
So, all data on that drive is lost and you'll have to go in and install an operating system.

Try using the live cd and running gparted to manually partition the disk.

Also, look into the mkfs.ext2 command.
(That is a very dangerous command that will destroy data. It will create an ext2 file system on the specified device.)

I hope that helps

---

### Post by jeremytodd1 on 2008-10-05
This is my first time trying to install Ubuntu so yeah...

How exactly do you run the gparted?

And also, I can't seem to get it to boot from disc anymore. I went into BIOS and changed it to boot from the disc first; didn't work. I got into the "boot from" menu and chose to boot from disc, still didn't work.

---

### Post by riahc3 on 2008-10-05
Next time do Wubi

---

### Post by jeremytodd1 on 2008-10-05
Whats that? 

And how do I get it to boot from disc?

---

### Post by jeremytodd1 on 2008-10-05
bump

---

### Post by miegiel on 2008-10-06
Something probably went wrong during the guided partitioning. The following should work if you want to erase everything on your disk.

Restart the installation. When you get to the step where you're asked if you want to use the guided or manual partitioning (there are 4 options in total but i don't know the other 2 by heart) choose the manual option. Now you will get a list showing your disks (sda,sdb, etc.) and partitions (sda1, sda2, ... sdb1, etc.)delete the partitions of the disk you want to install linux on. Next you will need to make new partitions on the empty disk. Make a 20GB (20000kB) partition ext3 partition for linux and set the mount point to / (root) and flag the format option. Then make a swap partition, 4GB is enough. Finally make ext3 partition in the remaining space and set the mount point to /home and flag the format option here too. From there on just continue the installation.

some side notes:
If you need to reinstall linux in the future you can just set the /home mount point without formating and without loosing the documents in your home directory (as long as you use the same user name). you'll only need to format the partition where you installed linux.
If you have a small disk (80GB or less) you can make the root partition smaller 10GB should still be enough. I'm using less than 4GB of the 20GB at the moment. And a 2GB swap partition should be enough too.
If you have a large disk (400GB or more) you can opt for making the linux partition a bit bigger but I don't think you'll need the extra space.

There is a gpatred live cd (a linux you can boot from cd without installing that only has the gparted partitioning program on it). You can use it to make, move and resize partitions in advance of installing ubuntu. You can get it at [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) (get the stable version). But during the ubuntu installation you will still need to select the manual option at the partitioning step to set the mount points.

I hope I didn't over complicate things :)

---

### Post by louieb on 2008-10-06
Are you trying to dual boot? Or install Ubuntu as your only OS?
Is there any thing on the hard drive you want to keep?

Any answer I could give would change depending on the answers to these questions?

---

