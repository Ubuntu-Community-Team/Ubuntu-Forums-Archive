---
title: "Ran FIXMBR to fix Win, but now can't boot UBUNTU"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by JBD88 on 2009-06-08
Seems like there is a lot of info on here about this, but I cannot find something to try:

C Drive on Win was full.  Downloaded a partition tool to extend it (Gparted would not do the Win C).  Made C bigger with free tool (Partition Manager).  When rebooted, got Error 17, could not boot either install.  Did some searches and decided to run FIXMBR to restore/remake the boot record???  Had a Win utility disk and got into a dos prompt and ran FIXMBR.  Now I get back to the screen to choose WinXP or UBUNTU.  Win works fine now, but Ubuntu goes to a screen that lists all the versions of Ubuntu (why does it list them all btw?) but none of them will boot.  Keep getting Error 17.  

So, using my basic skills, it seems the FIXMBR wiped the entry for Ubuntu in the boot record?  How do I fix?  How do I get the Ubu install recognized again?  

Joe

---

### Post by merlinus on 2009-06-08
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by keplerspeed on 2009-06-08
Thats right. Replacing the master boot record will allow you to boot win fine, but grub will be knocked out. So you will need to reinstate the GRUB, not the win MBR, as merlinus' link shows.

---

### Post by JBD88 on 2009-06-08
Tried the instructions.  Now it skips the first menu I used to get that just gives the generic choice of Windows or Ubuntu.  Goes right into the long list of all the various Ubuntu patch levels and then at bottom it has the Windows choice. So something happened.  However, when choosing the Ubuntu (top choice, latest release), it gives the 

Error 17:  cannot mount selected partition

I assume Win will still boot, I'll try that now.  In reading the article you referenced further, I tried to edit /boot/grub/menu.lst but there was no such file or even a grub dir under /boot.  I will continue to read it.  Appreciate any more help.

Joe

---

### Post by merlinus on 2009-06-08
If ubuntu is not running, you cannot access /boot/grub/menu.lst.

It may be that using something other than gparted screwed up something with ubuntu when you enlarged the windows partition.

Other useful info can be gained by booting from the live cd, and when running open a terminal and enter these commands:

```

sudo fdisk -l
df -h

```

---

### Post by merlinus on 2009-06-08
Sorry, posted in wrong thread.[]("http://pcsupport.about.com/od/fixtheproblem/ht/ntldrntdetect.htm")

---

### Post by JBD88 on 2009-06-08
Merlin,
Did you want me to run those commands?  you mentioned wrong thread.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x517c5a53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         784     6297448+  12  Compaq diagnostics
/dev/sdd2   *         785        3158    19069155    7  HPFS/NTFS
/dev/sdd3           22364       24321    15727635   83  Linux
/dev/sdd4            3159       21971   151115422+   f  W95 Ext'd (LBA)
/dev/sdd5            3159       21971   151115391    7  HPFS/NTFS

Partition table entries are not in disk order


ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1014M   17M  998M   2% /lib/modules/2.6.24-19-generic/volatile
tmpfs                1014M   17M  998M   2% /lib/modules/2.6.24-19-generic/volatile
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   64K 1014M   1% /dev
devshm               1014M   48K 1014M   1% /dev/shm
tmpfs                1014M   16K 1014M   1% /tmp
gvfs-fuse-daemon     1014M   41M  973M   5% /home/ubuntu/.gvfs
/dev/sdd5             145G  113G   32G  79% /media/disk

---

### Post by JBD88 on 2009-06-08
I forgot to mention, when I did the repartition, my linux-swap was a victim.  Does not exist and it won't let me recreate.  Would that be a contributing problem?

Joe

---

### Post by merlinus on 2009-06-08
You might try this:

```

sudo grub
root (hd3,2)
setup (hd3)
quit

```

Also, what is the boot order for your hdds in bios?

---

### Post by JBD88 on 2009-06-08
grub> root (hd3,2)

Error 21: Selected disk does not exist


right now I'm doing the last part of the article "The GUI Way"

Not sure what to do on #4 though, but it did let me recreate the swap at least.

The GUI Way: Using the Alternate/Install CD and Overwriting the Windows bootloader

   1. Boot your computer with the Ubuntu CD
   2. Go through the installation process until you reach "[!!!] Disk Partition"
   3. Select Manual Partition
   4. Mount your appropriate linux partions:
          * /
          * /boot
          * swap
          * ... 
   5.

      DO NOT FORMAT THEM.
   6. Finish the manual partition
   7. Say "Yes" when it asks you to save the changes
   8. It will give you errors saying that "the system couldn't install ....." after that
   9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
  10. Jump to "Install Grub ...."
  11. Once it is finished, just restart your computer

---

### Post by presence1960 on 2009-06-08
when you ran the command sudo fdisk -l, what happened to disks sda, sdb & sdc? they aren't listed.

we can go round & round and you can run a bunch of commands. lets put it all into one command to get the info on your set up. Boot into the Live CD and choose "try Ubuntu with no changes". download the Boot info Script to your Desktop. get it here: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

then open a terminal and run this command : > sudo bash ~/Desktop/boot_info_script*.sh This will create a RESULTS.txt file on your desktop. paste the contents of that file back here. highlight the text and click # in the toolbar to place code tags around the text

---

### Post by merlinus on 2009-06-08
In step #4, click on each partition, one at a time, and select edit, or right-click.  Then select the mountpoint for each (e.g. /, /home, swap), but make sure to not check the box to format them.

What confuses me, however, is that sudo fdisk -l returns sdd, which would indicate that you have a number of hdds.  It would be sda if you had only one.  Since numbering for these things starts at 0, and linux is on the third partition, that is why I had you enter (hd3,2) for root in grub.

---

### Post by presence1960 on 2009-06-08
> **merlinus said:**
> What confuses me, however, is that sudo fdisk -l returns sdd, which would indicate that you have a number of hdds.  It would be sda if you had only one.  Since numbering for these things starts at 0, and linux is on the third partition, that is why I had you enter (hd3,2) for root in grub.

+1

I caught that too. very strange indeed!

---

### Post by JBD88 on 2009-06-08
how would you feel if I just reinstall?  I can just use gparted to delete the linux partition, right?  then just reinstall in the same place?  I know that doesn't take that long, other than all the patching.  I don't have any data on there, just the O/S, so no bigger for me to just reinstall it.  Am I right aboutt he partition?  Just choose Delete from gparted before reinstalling?  If bad idea, I can run your commands.

---

### Post by presence1960 on 2009-06-08
> **JBD88 said:**
> how would you feel if I just reinstall?  I can just use gparted to delete the linux partition, right?  then just reinstall in the same place?  I know that doesn't take that long, other than all the patching.  I don't have any data on there, just the O/S, so no bigger for me to just reinstall it.  Am I right aboutt he partition?  Just choose Delete from gparted before reinstalling?  If bad idea, I can run your commands.

That would be your choice. Without the intention of starting a flame war, I would suggest always using the Ubuntu Live CD or the gparted Live CD to partition. Or if using Vista use it's disk management tool to shrink the partition.

Always defrag windows once or twice prior to resizing it's partition. That could be why you couldn't resize with gparted.
Whatever you decide we'll be glad to help if needed.

---

### Post by JBD88 on 2009-06-08
well, i tried gparted, first.  but it would not expand the win c drive.  refused.  and there was not enough space on C to defrag.  i can't wait to get rid of Win, but need it until I can afford a Mac mini.  Need somehting for my online poker habit :)  Tried it on Wine and the sound doesn't work and got tired of trying all the workarounds.  So, had to fish for the free partition tool which did work on the C drive, but got me in this mess.  The good news is, I actually got the partitions the way I wanted them now.  they were kinda jacked up before.  If I reinstall, i was going to go with 2 gb for swap (2 gb ram).  10 gb for /.  do I also need a /boot?  never made that one before.

---

### Post by merlinus on 2009-06-08
No need for /boot, but you may wish to create a separate /home partition, which will make installing a newer version (or reinstalling the current one) much easier down the road.

---

### Post by presence1960 on 2009-06-08
> **JBD88 said:**
> well, i tried gparted, first.  but it would not expand the win c drive.  refused.  and there was not enough space on C to defrag.  i can't wait to get rid of Win, but need it until I can afford a Mac mini.  Need somehting for my online poker habit :)  Tried it on Wine and the sound doesn't work and got tired of trying all the workarounds.  So, had to fish for the free partition tool which did work on the C drive, but got me in this mess.  The good news is, I actually got the partitions the way I wanted them now.  they were kinda jacked up before.  If I reinstall, i was going to go with 2 gb for swap (2 gb ram).  10 gb for /.  do I also need a /boot?  never made that one before.
/boot really not necessary unless you have an older BIOS that wont read past a certain sector on your hard disk.

I hear ya about windows. I only use it for work. Might boot into it 1 time per month. Just installed Ubuntu with wubi since I knew nothing about it's install process or what it is like. figured I could expand my Linux knowledge. Once I test it for a month or so I will uninstall it. At least I am putting my windows partition to use now!

---

### Post by presence1960 on 2009-06-08
> **merlinus said:**
> no need for /boot, but you may wish to create a separate /home partition, which will make installing a newer version (or reinstalling the current one) much easier down the road.

+1

---

### Post by merlinus on 2009-06-08
What are your impressions of wubi?  I have always thought it was a piss-poor excuse for not doing a regular install.  Sort of like spoonfeeding the masses, rather than offering an opportunity to learn about a wonderful os, make it run well, and solve problems, especially with the assistance of the forums.

My $.05 worth....

---

### Post by presence1960 on 2009-06-08
> **merlinus said:**
> What are your impressions of wubi?  I have always thought it was a piss-poor excuse for not doing a regular install.  Sort of like spoonfeeding the masses, rather than offering an opportunity to learn about a wonderful os, make it run well, and solve problems, especially with the assistance of the forums.

My $.05 worth....

It runs just as well as my 9.04 on it's own partition. It installs easily and was able to duplicate my installed software  on it. It runs well enough that I can't notice a difference between the two. BUT... I want to see how it will hold up when the windows file system does it's magic trick called fragmentation. I read in the documentation that will affect performance.

As for a poor excuse not to learn partitioning you are correct. That is my opinion also, don't want to start a flame war here. Even though I wiped my data on my first Ubuntu install it was worth it for two reasons: 1) it forced me to study about partitioning and what I needed to do to install an OS & 2) I had a backup of my data on an external USB HDD.

---

### Post by merlinus on 2009-06-08
Thanks for the info.  But since it basically is runnning on windows, is it not prey to the same vermin, spyware, viruses, and such?

BTW, when I first got into linux, I had to reinstall the os three or four times due to errors in commands, configurations, and the like.  Nothing like learning under fire...

It continues to be a wonderful process, as long as I view it as an adventure rather than a hassle.

---

### Post by sendblink23 on 2009-06-09
I don't think it can be a prey for that such, I had it on an older computer.. that suddenly was attacked by a virus, and still from BOOT OPTION when starting the computer Wubi still ran perfectly fine.. only the Windows start in was somehow affected (duhh a virus attack) <-- but ofcourse after that I simply ignored windoze and left it like that(never ran it again).. and kept using Wubi for a while.. untill that machine died of a beach accident (never take it surfing lol) :P

---

### Post by JBD88 on 2009-06-09
All,

Thanks for the help. I just reinstalled late last night and am back in action, for the better as it turns out.  Appreciate all the timely assitance.  Since I learned to keep data off the O/S drives, this is a pretty easy solution to anything I can't fix within a few tries.

Joe

---

