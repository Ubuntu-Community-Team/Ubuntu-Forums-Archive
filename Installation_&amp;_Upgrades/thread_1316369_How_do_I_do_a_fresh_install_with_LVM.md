---
title: "How do I do a fresh install with LVM?"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Captain_Glen on 2009-11-05
I am trying to do a fresh install of Ubuntu 9.10 onto LVM.

I have two 1TB hard drives.  

I have created 3 partitions.  

On the first hard drive I have a logical partition, which is the whole hard drive it is used as a physical volume for LVM.  

On the second hard drive I have a primary partition 255 MB used as ext4 with /boot as the mount point and it is bootable.

Also on the second hard drive I have a logical partiton, which is all the rest of the space.  It is used as a physical volume for LVM.

I have created a volume group called glen-desktop.

I have added both physical volumes for LVM partitions to the volume group so it is 2TB.

I have created two logical volumes: swap, which is 6GB and root which is all the rest of the space.

I have set swap to be used as swap space.

I have set root to be used as ext4 and has its mount point set to /.

I have then installed the OS but when it tries to boot.  It just shows a white Ubuntu logo for a while then goes black.  If I press a key it show the busy box terminal with the Error: only found 1/4 of meta data gave up waiting for root device.

I have tried putting the /boot partition on the first and second hard drive and it did not work.

I have also tried installing 9.04 but it gets the same problem.

I can't find any ubuntu guides on how to set up LVM.  What am I doing wrong?

Also in the past I did get LVM working with 9.04 but I can't remember how I did it.

---

### Post by Captain_Glen on 2009-11-06
Come on there must be someone who knows how to setup LVM?

---

### Post by owen_cook on 2009-11-13
I don't know the answer, but I *think* I have to go this way.

Background.
/dev/sda has 8 distros, normal partitions
/dev/sdb has 3 partitions, /dev/sdb1 ext3,  to be /boot when I get there
/dev/sdb2 swap
/dev/sdb3 with a stack of logical volumes, two I have set aside for /home and /

Boot up with the install CD
open a console and sudo apt-get install lvm2 (I think)
start the installer
switch to manual after the partitioner gets there and hopefully with lvm installed, it will see all your logical volumes.

I am only prepared to waste 30 minutes a day on this :) more tomorrow maybe

---

### Post by owen_cook on 2009-11-14
Well that was a waste of space/time 

The partitioner still didn't see the LVM on sdb, however the Administration->Disk_Utility does. 

Wonder what will happen if I mount them?

bbl

Now back!

I mounted /dev/mapper/karmic to /mnt/karmic and started the installion process over again

The partition was aware of the mounted partition, offering to unmount it for me.

I gracefully declined the offer and noted that as a result, no resizing etc maybe possible, but installation may be possible.

click Next and manual select

Still no sign in the partitioner.

I did note when running the partitioner separately, that it stated LVM was not yet available.

Oh well

If karmic had stayed with the regular old grub, I would have copied it across to the lvm and fixed the menu.lst

I see I can revert to old grub. Suse 11.2 is out and F12 due next week. see what they do with lvm

---

### Post by presence1960 on 2009-11-14
If you aren't doing so already the Live CD has no support for LVM, you must use the alternate text based installer. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by Captain_Glen on 2009-11-17
Okay I have fixed it.

I was setting up LVM correctly but there are a couple of bugs in 9.10 that screw things up.

If you want a complete guide on how to setup LVM on Ubuntu go here: [http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem]("http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem")

Please pay attention to the very last step it is the most important!!!

It says after installing 9.10, you must install lvm (sudo apt-get install lvm2)

Then you must chroot your /target (this is where the new OS is stored)
Do it with sudo chroot /target

Now you have tricked the Live CD into thinking it is installed.  Now all you have to do is install lvm onto the OS inside /target.  Now your new OS has lvm installed and can boot.

Just type sudo apt-get install lvm2.  It may say it is already installed.  If it is don't worry.  Just reboot and your good.

If you want to use the Alternate CD you still need the Live CD to do this last step for some reason.  I don't know why you didn't in 9.04.

EDIT: The last step for the ALternate CD is:
Boot live CD
sudo apt-get install lvm2
sudo pvscan
sudo vgchange -a y
mount /dev/your_volume_group/your_logical_root_partition /mnt
Mine was mount /dev/glen-desktop/root /mnt
sudo chroot /mnt
sudo apt-get install lvm2
sudo reboot

Also there is a bug in 9.10 that mounts raid arrays that you have deleted.  If this happens you won't be able to boot into LVM.  To fix it first turn off raid in your bios.  Then load up the 9.10 live CD and open gparted.  If you get a drive with a funny name like nvidia_ahahdhjdfsjkf then you have mounted a raid drive that you don't want.

To get rid of it, Open a terminal and type dmraid -E -r /dev/name_of_your_disk.  Note you want the disk name not the partition name.  You can see your disk names in gparted.  Mine was sda and sdb and my partition names were sda1 and sda5 and sdb1.  I had to do both sda and sdb.

Once you have erased the raid meta data you should see the funny named disk disappear after restarting gparted.

Once you have verified the raid disk is gone reboot and your OS should boot.

---

### Post by bobwdn on 2009-11-28
My experience with attempting to install onto LVM has been challenging. I am using a 9.10 "minimal CD" version. The partitioner is inverting the /dev/hda drive and labeling it /dev/hdi. The last drive instead of the first as it should be.

The incorrectly assigned label (hdi) is actually connected to the motherboard primary IDE as master. The remaining four other drives are connected to a Highpoint Rocket133 add-on card. These drives are being labeled (by the partitioner and then I guess Ubuntu) as hde (the actual master on the primary IDE connector), hdf, hdg & hdh. These are being identified properly (in my mind.)

I intend to use this computer as a backuppc server. This hardware is the equipment I have available to do this at this time. So, I will continue to look for a manual way to create the partitions and the LVM setup I need.

I am sorry, this post does not solve anybodys issue but, it may stop others from wasting time attempting to use the Ubuntu partitioner to do something it cannot do at this time. :-?

---

### Post by darkod on 2009-11-28
If you still need some help, there is quite decent detailed tutorial for LVM on 8.10 here but it would apply to 9.10 too:
[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

---

### Post by bobwdn on 2009-11-28
Thanks, darkod. I will go check that out.

To update my previous post (I had written from memory.) I just did a new install and the drives on the Highpoint are recognised as sda, sdb, sdc & sdd. And the drive that I indicated (above) as hdi is reconized as sde, the last of the five drives on my machine.

I am not sure yet but, I think I have a hardware issue. In creating the lvm, the lvm "program" complained that it could not write to sdc or sdd. I was given the choices of "retry, ignore or cancel." I choose *ignore* and now the partitoner has been creating the ext3 file system on the logical volume for about two hours. I think that that is long enough and I must consider other options.

Sorry, if I wasted anyones time.:sad:

---

