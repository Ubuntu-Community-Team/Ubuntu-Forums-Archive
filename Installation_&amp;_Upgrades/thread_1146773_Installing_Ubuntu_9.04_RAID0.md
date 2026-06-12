---
title: "Installing Ubuntu 9.04 RAID0"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by AnyWay on 2009-05-02
How do i install Ubuntu 9.04 in RAID0?

I've got:
- 2 HD, each one of 320gb;
- 4gb of RAM

I installed it, time ago, using Ubuntu 8.10 (Alternate), but now, with the 9.04 alternate installer (64 bit), i don't understand how to configure it.

How many partitions i have to create? And with which mount point? Is the swap partition needed? How to configure the RAID?

I'd need a tutorial step to step, as you probably understood i'm a beginner.
If you know a guide, i will read it, else i hope you can help me, thank you very much.

---

### Post by Crajy B on 2009-06-15
This is unfortunately all I could find.

Looks like installing to RAID in 9.04 is not as easy as it was in 8.10.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Did you find any better ways to install 9.04 on RAID-0?

---

### Post by H2SO_four on 2009-06-15
Configure your Raid from BIOS.  from there use the alternate cd for install.

---

### Post by AnyWay on 2009-06-30
No, i still haven't found anything :(

---

### Post by AnyWay on 2009-07-20
Note that i'm talking about Fake Raid, as in my BIOS there is nothing about Raid (i've also tried upgrading the BIOS).

I've tried installing it from Ubuntu 9.04 Alternate CD, the installation goes, but, at the reboot, i get:
 
Missing operating system, before Grub's menu.

What could be?
Thanks

---

### Post by BIACS on 2009-08-08
Here's what I did on my laptop with Ubuntu 9.04 Alternate. My laptop has two 500 GB SATA's and are setup as the following
/sda1 100mb for /boot
/sda2 496gb raid0 /
/sda5 4gb raid0 swap

/sdb1 496.1 raid0 /
/sdb5 4gb raid0 swap

(non formatted size) 
992gb Raid0 (file system)
8gb swap

Here's how I did it

Boot with the alternate disk
Get to the partition disk section
Go to the FREE SPACE under your first disk
Click on FREE SPACE and select 'Create a new partition'
Specify the size you want for your /boot partition (100mb is plenty)
On the next page scroll up to 'Use as:' and hit Enter
Set the partition for /boot to be Ext3. Change 'Mount point:' to be /boot. Scroll down and click 'Done setting up the partition'

Next click on the remaining FREE SPACE
Set the size you want for the File System. Remember to reserve enough space for the swap to be at least 1.5x your RAM, you can calculate 1/2 that amount from each disk. Meaning, I left 4 GB of each disk so when the two 4 GB partitions are combined as RAID 0 they will provide the system with an 8 GB swap. I have 4 GB RAM so I needed at least 6 GB for swap.

Specify Primary partition for the partition you are creating for the file sytem.

Now go up to the 'Use as:' and set the partition to 'physical volume for RAID'

Turn on the bootable flag.

Click 'Done setting up the partition'

Repeat the above steps to create the remaining space, again set it to be used as physical volume for RAID. It will automatically specify that it is a Logical partition.

Once you are done with the FREE SPACE on your second drive you will be back at the partition disks screen and you will see 2 raid partitions under each disk and a /boot under your primary drive. 

Go up to 'Configure software RAID' hit Enter. Select Yes to confirm changes to your disks.

Hit Enter on 'Create MD device'
Specify RAID0
Use space bar to select /dev/sda2 and /dev/sdb1 (or your equivalent). Just be sure the partition you select is the one designated for the file system
Select Continue and repeat the process for RAID0 with the two remaining partitions. 

Now scroll down to RAID0 section on the screen. Move to the space designated for your file system and hit Enter. Go to 'Use as:' and choose Ext4. Go to format the partition and hit Enter. Choose / for the mount point. Click Done and move to the next RAID0 section, hit Enter and set the 'use as:' to be swap.

Once your done setting the / and swap, go to the bottom of the screen and select Finish. You will be prompted again to confirm that you want to save the changes and modify the disks.

The process of formatting will begin followed by the rest of the setup. 

I was able to setup RAID1 and RAID5 with drives on my Desktop with no /boot partition but when I attempted RAID0 on my Laptop I kept getting a GRUB error (#2 and #26) on the first boot attempt. By using a boot partition it started fine. I was also able to setup LVM on the Laptop and boot with the LILO but I wanted to use RAID (mostly stubbornnes)

Good luck.

---

### Post by haider_up32 on 2009-08-15
Q1.i have configured raid0 and installed winxp on raid0 ..i have installed ubuntu on non-raid disk ...how will ubuntu 9.04 recognize my raid array?? currently it shows both raid0 drives as separate disks

Q2.What is dmraid? i have installed it but does it do??

---

### Post by begoogled on 2009-08-31
Wow! Thanks a million! I have spent the last week banging my head against a brick wall trying to get RAID working on my box. I am a bit of a newbie to linux so I think I just had my bootable flags on the wrong partitions.. haha.. I put it on the /boot partition instead of the / partition of the RAID0! Doh!

Anyway, thank you very much for this post. It has solved the software RAID issues I was having!

---

### Post by begoogled on 2009-08-31
Hi guys. Back again. I am new to Linux/Ubuntu and wanted to contribute back by writing the walkthrough below as it took me so long to figure out how to do this and I figure it may help other people save some time.

Basically it shows how to set up a single-boot Ubuntu system with a 5TB encrypted RAID that functions as pretty much the sole drive (heh.. plus a small /boot partition ;))

My system is:
Intel core i7 920
Asus P6T Deluxe V2 motherboard
12GB DDR3 RAM
5x 1TB Seagate Barracuda harddrives
Gigabyte GTX275 video card
Optical drive yada yada yada

Operating system to install
Ubuntu 9.04 Alternate CD

The problem:
The motherboard has FakeRAID but after following every single tutorial and HowTo I could find online, the partition manager in the Desktop and Alternate CDs would not recognise any drives were actually present to partition.. Hence I was stuck at setup.
I decided to set it up as linux software RAID but also wanted the added security of drive encryption so if someone steals my computer they cant use any data from the drives. (Regular backups also ensure that I dont LOSE the data if the computer goes AWOL). Anyway, the walkthrough for my solution is shown below. Feel free to ask questions. I am relatively new but I will help with whatever I can. Good luck and I hope it saves you some time.


TO START WITH

1. Boot with the 9.04 Alternate CD until reaching the partition manager. (If you are prompted by message saying 'Activate Serial ATA RAID devices?', simply select no as we will set up software RAID in the partitioning).
2. Select Manual partitioning
3. Select the first hard drive and create a new empty partition on the drive.
4. Repeat this for each drive.


SETTING UP THE /boot PARTITION

1. Under the first drive select the FREE SPACE.
2. Create a new partition.
3. Partition size 200MB. (I chose this figure on what I read online. Opinions may vary)
4. Select Primary type
5. Select Beginning
6. Use as: Ext3 journaling file system
7. Set Mount Point to: /boot
8. Bootable flag: on   (I'm not sure if this is needed as linux looks like it resets it to off again later.. heh.. dont shoot me - I'm a newbie telling you how I fixed the problems that plagued me in setting up this 5TB raid :)
9. Done setting up this partition



SETTING UP THE RAID PARTITIONS

1. Under the first drive, select FREE SPACE again.
2. Create a new partition.
3. Partition size 999800MB
4. Select Primary type.
5. Select Beginning.
6. Use as: physical volume for RAID
7. Bootable flag: ON
8. Done setting up the partition.
9. Repeat this process for each other drive by selecting the "FREE SPACE" under each drive and creating the RAID partition using the same steps and settings as for the partition just created.



SETTING UP THE REMAINDER OF the RAID + ENCRYPTION + LVM

1. In the main partitioning menu, scroll to the top and select "Configure Software RAID"
2. Select Yes when asked to write the changes to the storage devices and configure RAID.
3. Select "Create MD device".
4. Select RAID0.
5. Select all the volumes and continue.
6. Select Finish.

7. Select the Space under the RAID0 device. (It should say something like... "#1     5.0 TB").
8. Use as: physical volume for encryption
9. Select Done setting up this partition.


10. Scroll to the top of the partition manager and select "Configure encrypted volumes".
11. Type your nice, long and hard to guess password and then type it again to confirm it.

12. Select the line under "Encrypted volume". It should say something like " #1  5.0 TB   f   ext3".
13. Use as: physical volume for LVM
14. Done setting up this partition.

15. Scroll to the top of the partition manager and select "Configure the Logical Volume Manager".
16. Select Yes when asked to write the changes to disks and configure LVM.
17. Select Create Volume Group and give it any name you want. I just called it "lvm".
18. For the devices for the new volume group, select the encrypted volume you have just created. That was the only option that showed up for me.

19. Now we want to set up our root and swap partitions as follows:
20. Select "Create Logical Volume".
21. Select the volume group you just created.
22. Logical volume name: swap
23. Logical volume size: 24GB  <-- I just used the formula of the swap being twice the size of the installed RAM).
24. Select "Create Logical Volume" again.
25. Select your volume group again.
26. Logical Volume name: root
27. Logical volume size: (the rest of the disk.. Linux should show this by default) It was 4974994MB for me :)
28. Select Finish

29. Back in the partition manager, select the lvm root partition you just created.
30. Use as: Ext4 journaling file system  (Heh.. please dont flame me. If you want to use Ext3 please feel free :P)
31. Mount point: /
32. Done setting up the partition.

33. Back in the partition manager again, select the lvm swap partition you created.
34. Use as: swap area
35. Done setting up the partition.

36. Scroll ALL the way back down to the bottom of the partition manager and select "Finish partitioning and write changes to disk"
37. Select Yes to write the changes to disks.


Congratulations, you have just saved yourself the 4 days it took me to figure out how to do the above starting from scratch and cobbling online info together! Your installation will now continue as normal and you will end up with a bootable system that has a nice, big super-speed 5TB RAID as your main drive!

---

### Post by begoogled on 2009-09-11
As an extra piece of follow up, I have come across one issue since my post. The RAID0 speed seems to be running at about 105MB/sec whereas each individual drive, when tested, runs at about 125MB/sec... The only explanation I can find so far is that the maximum encryption bitrate (ie the max speed of encryption) is about 110MB/sec for my system.. So, even if the RAID0 could run faster, it is limited by the encryption speed.. I am not entirely sure if this is the explanation, but it is the only one I have come across..

That said, I did previously run the system as a RAID0 without encryption/lvm and it did run much faster, so it probably is the encryption speed that it the limiting factor..

If anyone else has any ideas, any suggestions for me to test are welcome :)

---

### Post by PFree on 2009-12-14
> **begoogled said:**
> Congratulations, you have just saved yourself the 4 days it took me to figure out how to do the above starting from scratch and cobbling online info together! Your installation will now continue as normal...

Hi begoogled,

Thanks for putting the Install instructions together! I've been trying to install Ubuntu for a week now. I finally gave up on 9.10 because I absolutely could not get that version to install. Then, I decided to try 9.04; did a search on 9.04 install instructions and your post popped up in the search results.

I am entirely grateful to have found this thread. The installation wasn't what I wanted, but your instructions are the only instructions I could find on the entire internet THAT ACTUALLY WORK.

Now that I have a system to work with, I can start researching how to install it as a REAL raid system. It sucks that I'm using a mobo with a ICH10R Controller that I can't  take advantage of (yet). At least I have a OS to work with for now.

I sent you a PM. Check it out.

Thanks again!

Regards,
Paul

---

