---
title: "install grub to boot sector of a partition using ubuntu live cd"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by andylinux on 2009-03-29
I like to use unetbootin to install ubuntu desktop (live cd) using a usb drive.  This is very useful for testing.  I also use the GAG boot loaded on my master boot record.  Thus when installing I need to install grub to the boot sector of the partition.  However the recent versions of the Ubuntu live installer no longer have the option to do this.  You can pick the option to install to the master boot record or not install grub.  I wish they option would not have been removed.  

So when I do the live cd install I tell it not to install grub but then I cannot figure out how to install grub manually after the fact to the boot record.  All the grub installs howtos I found searching the forum refer to fixing a grub install but on my system grub is not installed at all.  

The closest I got was to do the following,
Boot live cd,
sudo mkdir /mnt/root
sudo mount /dev/sda5 /mnt/root
sudo sudo grub-install --root-directory=/mnt/root /dev/sda5
This seems to work as I now have a grub directory in /boot/ of my new installation.  However when I boot I just get a grub prompt because I don't have a menu menu.lst file.

Any suggestions?  I know I can do the install using the alternative cd but I hate having to burn a new cd everytime and the live install using from usb is much faster then cd.
Thanks for the help.

---

### Post by Elfy on 2009-03-29
Try this to install grub

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

As far as > I wish they option would not have been removed. I didn't think they had, when you get to the final part of the install go advanced and tell it where you want grub installed to.

---

### Post by andylinux on 2009-03-29
Thanks for the suggestion.  In all my searching I had not found that link to the ubuntuguide.  Bad news it is didn't work.  My problem is that most information I find on the internet talks about reinstalling grub.  But in my case grub is not installed because during the live installation I went to the advanced option and unchecked the box to install grub.  

When I ran grub-install I got the message that grub wasn't installed so I apt-get install grub and then ran 
grub-install /dev/sda5
Could not find device for /boot: Not found or not a block device.

In the past if I went to advanced I thought there two options one to install to /dev/sda and one to install to the partitions boots section such as /dev/sda5.  But with the Jaunty Kubuntu amd64 live beta install I don't see the option anymore.

---

### Post by andylinux on 2009-04-03
Just to follow up, I gave up and burned the alternate CD and installed it that way.  If anyone has a suggestion of how to install the alternate cd using a usb thumb drive instead of burning a cd I would love to know.

---

