---
title: "Install from hard drive"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by thezood on 2009-01-14
Hi,

I'm trying to install Intrepid on my netbook. First of all, I know there are netbook releases out there but I'd like to try and install vanilla Ubuntu because I'm not sure the netbook variants are the way to go. I do not want to repartition anything and I only want to format the root partition. 

Anyway, the computer doesn't have a CD-ROM reader and I thought I'd save some money by installing from a hard drive partition instead of bying an SD card. Yes, I'm a cheap *******. :) This is my partitions:
sda1 10Gb ext3 mounted as /
sda2 8,5Gb ext3 installation media & boot partition
sda3 1.5Gb swap
sda4 60Gb ext3 mounted as /home

The problem is, there is a bug in the Ubuntu installation program (alternate CD) that makes the partitioner not list any partitions if any partitions on the disk is mounted ([https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/290415](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/290415)). Obviously, I need a partition mounted since I'm using one to store the installation .ISO. So I figured I could unmount all partitions while the partitioner works and then re-mount sda2 when it wants to copy files. This actually did work but with a hitch: the partitioner did not recognize any of my partitions as having file systems! They were listed as being broken or having no file systems at all. I had to manually select what types file systems they should be, and I'm sure the program would have formatted them had I gone any further.

So my question is: do anyone know if there IS a way to install Ubuntu from a partition on the same hard drive as /? Or do I have to spend my precious ten bucks on an SD card? :)

---

### Post by jerrylamos on 2009-01-14
Live Ubuntu can be run from CD, DVD, USB, or even a hard drive partition.  See
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

The Live CD is also known as the "Desktop Installer". It is the default Ubuntu installation CD. The ISO you downloaded has the name "desktop" in its name, these are the instructions to use. 

UNetbootin is a utility that can do much of the following automatically.  In the forums some people have luck with UNetbootin, some don't.  I prefer to roll my own as follows.

If you already have a working linux system, installing without external media is easy. You need to create a new partition, copy the CD contents over to it, boot from the new partition, and proceed as if you were installing from a CD. Note that you can't use what will be the root partition for the CD contents, as the installer is stubborn on formatting it (it will fail).

The benefits of installing without external media are that it can save you time if you are already familiar with the process, and you get a very usable system upon booting into the installer because it is running from a hard drive rather than a CD.

Step 1. Use gparted to create a new primary partition and format it to ext3. You need slightly more than 700MB of free space on it. 750MB should be sufficient unless the .iso is oversized.  In that case add about 50 mb to the .iso size. Let's say the name of the partition is /dev/sda1. If your new ubuntu install is going to coexist with your old system, you might find it convenient to create a partition for your new system as well at this point using gparted.

Step 2. Copy CD contents over to the new partition using the command

 mkdir /tmp/install_cd
 sudo mount disk-image.iso -o loop /tmp/install_cd
 sudo mkdir /mnt/installer
 sudo mount /dev/sda1 /mnt/installer
 sudo cp -r /tmp/install_cd/* /mnt/installer
 sudo cp -r /tmp/install_cd/.disk /mnt/installer
 sudo umount /tmp/install_cd

Replace the name of the iso to whatever you downloaded and /dev/sda1 with whatever your new partition is.

Step 3. Edit your grub configuration file (typically /etc/grub.conf or /boot/grub/menu.lst) to boot from the new partition by adding the lines

title           installer
root            (hd0,0)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd          /casper/initrd.gz

Note, on a 512 mb memory system I use 384000 for the ramdisk size.

The first line after the title tells grub which partition contains the installer. hd0 stands for "first hard disk," and the 0 following it standards for first partition. You will need to change this if your installer partition is different from /dev/sda1. sdaN becomes (hd0, N-1), sdbN becomes (hd1,N-1) and so on. As you can see, grub starts counting from 0, which can be confusing.

Step 4. Reboot, and choose "installer" from the grub boot menu, and continue as if you were installing from CD only much faster.

If you want to continue to run the install CD, you can create a partition say 512 mb, format ext3, label casper-rw.  Then add the word persistent to the kernel line.

I make the above steps into executable text files.  That way testing a new .iso is much much faster than writing CD's or USB's, and run almost normal speed.  Do note if you install another .iso you need to re-format and re-label the casper-rw partition.

Jerry

---

### Post by thezood on 2009-01-14
It was that easy? I read somewhere that you have to use the alternate CD as the Live CD supposedly can't boot from a hard drive. I didn't even try it. Silly me. :) People really talk out of their bottoms alot about these things. I'm going to try this right away!

---

### Post by thezood on 2009-01-17
...And now I have another problem: [http://ubuntuforums.org/showthread.php?t=1042111](http://ubuntuforums.org/showthread.php?t=1042111)

To quote C3P0: "will this never end?" :)

---

