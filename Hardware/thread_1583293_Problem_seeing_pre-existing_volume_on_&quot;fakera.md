---
title: "Problem seeing pre-existing volume on &quot;fakeraid&quot;"
date: 2010-09-27
forum: Hardware
---

### Post by hnascimento on 2010-09-27
Hey everyone!

I'm done a couple of searches, but I'm a bit lost... 

I have a dual-boot situation between Windows 7 and Ubuntu 10.04 on a 500GB SATA drive. Everything is fine and dandy.

However, I also have a FastTrak TX4310 SATA RAID board, which apparently is a "fakeraid". I have 3 disks connected to it, forming a RAID5 volume, formated with NTFS. The RAID is done via hardware, so Windows sees it as a regular disk. The RAID5 volume is a completely secondary one, as it doesn't host any system or boot files (either Win7 or Ubuntu). I have all my "goodies" there: movies, games, music, etc.

The problem is that I can see the controller on Ubuntu, and I can see the individual physical disks. And I think I can see the actual partition, but it's marked as "unknown" on the Ubuntu "Disk Utility".

All the info I find about the "fakeraid" seems to be related with installing Ubuntu on the actual RAID, but that's not my case, I just want to access my "goodies" on Linux :(

Can someone point me to the right direction? :) Thanks in advance! ;)

---

### Post by darkstarbyte on 2010-09-27
I know how to fix your problem. You need a shell script to set this up for you. I well go find one off of Google if I can't I will either ask a system administrator if they can write one or I will post and tell you.

---

### Post by darkstarbyte on 2010-09-27
Well I took a look into the problem. There is a way to solve it its a kernel module or something, but you will need to back up your files, because it can dangerous to your existing data. I will see if I can sum it up, here is the link. 

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by darkstarbyte on 2010-09-27
Well, I hope this helps.


 MAKE SURE YOU BACK UP ANYTHING OF IMPORTANCE!!! 

This Section shows you how to install Ubuntu using the Ubiquity graphical installer found on the Live CD. 
If you need more information about any given read any of the additional information below 
Boot the Live CD 
Open a terminal 
Enter the following commands 
(skip the first one if you are doing RAID 0 or 1) 

$ sudo modprobe dm-raid4-5 

$ sudo apt-get install -y dmraid 

$ sudo swapoff -a 
disables erroneous use of the backing swap partitions if you are reinstalling 

$ sudo dmraid -ay 
Now check that you can view the partitions in the raid array with this command 

$ ls -l /dev/mapper/ 
OUTPUT: 
control             isw_beeaakeeaa_five

we will be using the array /dev/mapper/isw_beeaakeeaa_five in this example. 
Create partitions on your raid array with your preferred partition manager, or do so using the partitioning tool provided in ubiquity (partitioning with ubiquity installer have not been tested) 

$ sudo cfdisk /dev/mapper/isw_beeaakeeaa_five 

We used /dev/mapper/isw_beeaakeeaa_five5 partition as Ubuntu root partition in this example. 
Begin the install process 
If doing a guided install make sure you select the raid partition. if you are going to do a manual install make sure you do not create a partition on any of the disks that make up the raid partition. 

On the last step before installing, click the Advanced options and uncheck the install boot loader option. We will install grub (the boot loader later). 
After installer finishes, close ubiquity installer without rebooting the machine. 
Install dmraid and grub in your new Ubuntu installation: 

$ sudo mount /dev/mapper/isw_beeaakeeaa_five5 /target/ 

if this fails maybe the /target directory is already mounted if not then some debuging will be required. If any more information can be provided related to this issue place add your knowledge to this document 

$ sudo mount --bind /dev /target/dev/ 

$ sudo mount -t proc proc /target/proc/ 

$ sudo mount -t sysfs sys /target/sys/ 

$ sudo cp /etc/resolv.conf /target/etc/resolv.conf  

$ sudo chroot /target/ 

# apt-get update  

# apt-get install -y dmraid 

# apt-get install -y grub 

# mkdir /boot/grub 

# cp /usr/lib/grub/x86_64-pc/* /boot/grub/ 

# grub --no-curses you will now be at the grub prompt grub> 

 grub> device (hd0) /dev/mapper/isw_beeaakeeaa_five 

 grub> find /boot/grub/stage1  
OUTPUT: 
find /boot/grub/stage1
(hd0,4)

make a note of the output from this command it will be needed later. in my case I have my linux partition as the first extended partition you most likely will have different results (remember that grub starts partition numbers in zero, so partition 5 for linux is partition 4 for grub). 

 grub> root (hd'x','x') 

replace 'x' with the partition number from the previous step 
Install grub on your disk (or partition if you prefer boot your computer with another boot manager) 

 grub> setup (hd'x')  

replace 'x' with the values gathered in the previous step 
or 

grub> setup (hd'x','x') to install grub on the partition. 

YOU WILL NEED ANOTHER BOOT MANAGER TO START YOUR COMPUTER 

 grub> quit 

# update-grub 
say yes to creating a menu.lst 

now open the newly created menu list and make the following changes. Any editor can be used it is not required that you use nano # nano /boot/grub/menu.lst 
Change 

# groot=(hd0,0) TO # groot=(hd0,'x') 

root option in the boot entries to root (hd0,'x') Replace the 'x' with the partition that was found earlier 

Add the Windows boot entry if need be. 
  title                 Windows
  rootnoverify (hd0,0)   # use the correct partition for Windows, of course
  makeactive
  chainloader +1

For all Ubuntu-related boot entries, such as 
   title         Ubuntu ...
   root          (hd0,0)
   ...

change (hd0,0) to (hd'x','x') (in my case, Linux partition was not the first one, and without these changes I would get grub "Error 17" after reboot). You can use the uuid of the mapped raid partition in a grub menu.lst uuid field instead of the root (hd'x','x') field; look in /dev/disk/by-uuid with 'ls -l'. 
Save and exit nano. or what ever text editor you are using. 

# update-grub 
make sure the new install of Ubuntu loads the raid module kernel 

# echo dm-raid4-5 >> /etc/initramfs-tools/modules 

# update-initramfs -u 

# nano /etc/modules 
and add 'dm-raid4-5' if not exists 
Reboot and verify both Ubuntu and the existing Windows partition boot if Windows is installed.

---

### Post by hnascimento on 2010-09-28
Hi darkstarbyte :)

Thanks for your help :)

However, this seems to be the workaround to install Ubuntu onto a "fakeraid" volume, as it mentions the install process and boot loaders and whatnot. But I'm gonna take a look at the commands, and see if the ones I need are somewhere in there, and I'll report back :)

Thanks again!

---

### Post by hnascimento on 2010-09-28
Ok, so I've tried this part, which seems to be more or less what I need:

#sudo dmraid -ay

However, I get the following as an output:

ERROR: pdc: zero sectors on /dev/sdd
ERROR: odc: setting up RAID devide /dev/sdd
ERROR: pdc: zero sectors on /dev/sdc
ERROR: odc: setting up RAID devide /dev/sdc
ERROR: pdc: zero sectors on /dev/sdb
ERROR: odc: setting up RAID devide /dev/sdb
no raid disks

This is consistent, as the three disks mentioned correspond to the disks that make up the RAID5. However, it seems as if Ubuntu can't read what's actually on the disks...

If I go to the "Disk Utility", on 2 of the disks I can see that the system recognizes there is a RAID volume in there, but on the 3rd, it just says "not partitioned".

I'm pretty sure the RAID5 volume is intact, because if I boot into Win7, all the stuff is right there. It just seems that Ubuntu is having a hard time reading the pieces of the puzzle. Do you think is there anything I can do, short of recreating the RAID from scratch?

---

### Post by ronparent on 2010-09-29
If you type dmraid -l in a terminal you will see a list of all fakeraid controllers and levels of raid supported. There appears to be no pdc support for raid 5. Odc is not in the list! Outside of this it appears you would need a manufacturer supplied linux driver to access the raid5.

---

### Post by hnascimento on 2010-09-29
> **ronparent said:**
> If you type dmraid -l in a terminal you will see a list of all fakeraid controllers and levels of raid supported. There appears to be no pdc support for raid 5. Odc is not in the list! Outside of this it appears you would need a manufacturer supplied linux driver to access the raid5.


Yeah, I was getting to the same conclusion :(

I've searched the Promise site, and I can find some linux drivers, from 2006 :( For RedHat and Suse... You think I should give it a shot, or would I just get into more trouble, as the drivers are 4 years old? :)

---

