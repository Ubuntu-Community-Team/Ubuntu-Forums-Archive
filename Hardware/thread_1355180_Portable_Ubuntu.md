---
title: "Portable Ubuntu"
date: 2009-12-14
forum: Hardware
---

### Post by bower4311 on 2009-12-14
I want to purchase some form of a portable Ubuntu to get used to using it. I had it as a live version on a flash drive but something went wrong and my flash drive was ruined. I want to be able to use it as a full OS with all of my information on it. I want to be able to plug it in from computer to computer so I'd assume the best way to go is USB.

I've been looking at portable hard drives but they seem so expensive. Is there a cheaper alternative. I don't need tons of space, not that much at all. Even under 50-100gb is more than enough. 

Is there any cheap hard drive I could purchase or should I buy a high quality large USB drive?


Thanks

Adam

---

### Post by goldshirt9 on 2009-12-14
what currency are we talking about.:D

---

### Post by bower4311 on 2009-12-14
> **goldshirt9 said:**
> what currency are we talking about.:D

USD If thats what you mean, but I want my price range around $50-75 which may limit my possibilities a bit.

---

### Post by Chesamo on 2009-12-14
The problem with Flash memory is that is has a limited number of read/write cycles that it can support before failing, so let me say that I do not recommend running a full install off of a Flash drive.

That being said, NewEgg has some very nice and inexpensive drives.
[http://bit.ly/8eV2dg](http://bit.ly/8eV2dg)

---

### Post by goldshirt9 on 2009-12-14
I'm from the UK so my answers are useless for you.
portable / pocket hdd are cheap here . 
i imagine their even cheaper in the usa

---

### Post by rokytnji on 2009-12-14
I run Puppy, AntiX, and Ubuntu off of SD Flash Drives and USB Flash. All persistent installs. Not live. Making a live USB or SD flash is simple. Lots of documentation on it and live will run in Fat32 file system. All my persistent installs are done with EXT2 file system with no swap .  For a persistent install, just boot up live cd,usb,or sd card and point the installer to the flash drive of your choice. Below is a writeup I did for AntiX.

[http://yatsite.blogspot.com/2009/07/install-antix-82-final-on-asus-eee-900.html](http://yatsite.blogspot.com/2009/07/install-antix-82-final-on-asus-eee-900.html)

---

### Post by bower4311 on 2009-12-14
> **Chesamo said:**
> The problem with Flash memory is that is has a limited number of read/write cycles that it can support before failing, so let me say that I do not recommend running a full install off of a Flash drive.

That being said, NewEgg has some very nice and inexpensive drives.
[http://bit.ly/8eV2dg](http://bit.ly/8eV2dg)

Yeah that was the reason why I didn't want to do a full install on a flash drive.

---

### Post by bower4311 on 2009-12-14
> **rokytnji said:**
> I run Puppy, AntiX, and Ubuntu off of SD Flash Drives and USB Flash. All persistent installs. Not live. Making a live USB or SD flash is simple. Lots of documentation on it and live will run in Fat32 file system. All my persistent installs are done with EXT2 file system with no swap .  For a persistent install, just boot up live cd,usb,or sd card and point the installer to the flash drive of your choice. Below is a writeup I did for AntiX.

[http://yatsite.blogspot.com/2009/07/install-antix-82-final-on-asus-eee-900.html](http://yatsite.blogspot.com/2009/07/install-antix-82-final-on-asus-eee-900.html)

Would you suggest a certain flash drive of higher quality that will be reliable. My Sandisk is useless now, it only holds 1.9mb instead of 1.9gb which is a joke. I barely used it but it messed up when I installed ubuntu as a live install.

---

### Post by rokytnji on 2009-12-14
Sandisk comes with that U3 software. First thing i do is use my wifes Window computer (I don't ryb windows) and use the U# uninstaller supplied by sanddisks site.

The software (U3) interferes with installs. After unistalling U3 software. Reformat the sandisk as fat32. I would use the Unetbootin for Windows version since you run Windows to install Ubuntu iso to the flashdrive. Or you can try ther Ubuntu Intaller to USB though I have never tried it. I have the Linux Version of Unetbootin and after installing mtools and P7zip-full. It works great for me. Your pendrive might not be broke. 
[U3 unstaller]("http://www.u3.com/support/default.aspx#CQ3")
[HP Format Tool]("http://files.extremeoverclocking.com/file.php?f=197")
[Unetbootin for Windows]("http://unetbootin.sourceforge.net/")

---

### Post by rokytnji on 2009-12-14
By the way, I like the Kingston Data travelers. They are cheap. You can format them again after breaking open the package and it wipes the software right off without need to run a uninstaller.

For flash SD cards I use the cheap Dana Electric.

---

### Post by bower4311 on 2009-12-14
Thanks for the help, I fixed my current flash drive. What is your suggestion for the best way to partition it, I'm assuming I should do this while Ubuntu is loaded. I used Unetbootin and am currently using ubuntu off of my flash drive. 

Which tutorial or program would suit me best to partition it?

I'm using 9.04

---

### Post by C.S.Cameron on 2009-12-15
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

However if you want a full install, like you would get with an internal hard drive, just plug in a USB stick, 4G or larger, disable the internal hard drive and run install from the Live CD, (ubiquity). You can even use manual partitioning if you want a separate home partitioning. With this method you can update without quickly filling your stick.

I have been booting Ubuntu from flash drives for years and have never had one fail from over use, Nor have I ever read of one actually failing in real life due to running Linux. I think this is only a myth.

---

### Post by bower4311 on 2009-12-15
So if I bought a large USB drive you think I would be able to run ubuntu as an operating system opposed to a live CD, without any troubles?

---

### Post by wilee-nilee on 2009-12-15
I just bought a 16 gig Kingston and partitioned it 1st with gparted into one extended and one fat32. In the extended I put a ext4 primary then the swap, then booted from a live ISO of Lucid on another thumb and did a full install on the Kingston with the regular installer. You can turn off the main HD in Bios I think but I just use the manual install and make sure everything is pointed at the correct partition to install including the grub install on to the stick. 

There is a slight delay in using Firefox I am not sure if it is associated with Lucid. I have used a usb creator loaded ISO with persistent and had little or no delay with Karmic.

---

### Post by C.S.Cameron on 2009-12-15
You can do a full install on a flash drive as small as 4GB. Ubuntu runs a bit slower on a cheap flash drive than on HDD, This will probably be reversed with USB 3.
The only problem I have found is that if the flash drive gets filled it will no longer boot until some data is removed.
If you wish to use the FAT32 partition for transferring data to or from a windows machine, it should be the first partition.

---

