---
title: "Adding Slave Hard Drive"
date: 2010-09-25
forum: Hardware
---

### Post by Gameboyman99 on 2010-09-25
Hi again, I'm just the problematic person:
So I want to add a 2nd hard drive(Seagate Barracuda ATA IV ST340016A) and it shows up in Device Manager(both Ubuntu's and Window's), but it won't show up in (My)Computer. Device Manager says the device file is in **/dev/sdb**, but no idea what that means because when I click that file it says **Could Not Display "/dev/sdb". There is no application installed for block device files.**
  Sooo, now what??
Thx,

---

### Post by mrhhug on 2010-09-25
its still unformatted (how most drives come) you can fdisk to format it(command line), if you want windows to be able to easily read if i suggest NFTS(a windows filesystem), windows won't like to play nice with ext3(a linux filesystem) but ubuntu's pretty awesome with their NTFS support

you can install gparted(GUI) in ubuntu, its pretty easy to use gparted - this is a formatting app

in the windows device manager when you select the disk to the right it should say unformatted or RAW or something like that (its been a while for windows) just right click on that "unformatted" and hit format and windows will format it NTFS

if you have formatted it NTFS then you'll need to install some NTFS viewing software - try this walk-through: [http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)

*you'll only need to format it once i just wanted to give you both a linux and windows solution

---

### Post by endotherm on 2010-09-25
it sounds like your device does not have a partition/volume. if you open up gparted (you may need to install it first), and select the drive, does it show any volumes/partitions? if not you can create one via gparted. 

once you have the drive mountable, you will have to add it to your /etc/fstab file to have it automatically mount on boot. here are some instructions on how to do that.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by Gameboyman99 on 2010-09-25
Huh... it might be, but I think it has Windows 98/2000/ME, yes, I will double check that...
Being the lazy person I am I did not check to see if it wuz formatted, but Gparted is awesome! Yayyyy! new 40GB Hard disk is listed in Computer!
Thx guys!

---

