---
title: "/cdrom won't unmount while partitioning and installing ubuntu super OS from hard disk"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by VACSecured on 2009-08-11
i curently have xubuntu Xfce installed on my computer, and i am trying to swithch to ubuntu super OS using the program unetbootin and installing the ISO right on the hard drive. (i also tried this with mint linux and got the same error) i can get in the instalation menu and partition it, but when it starts to install i get and error that says it cannot unmount /cdrom please close all programs using it and try again. so i am no computer wiz or linux wiz for that matter, i am just getting into linux and i am still trying to learn as much as i can, but from what i do no i have tried to go into the terrminal and using the bash command "umount" mannually unmount /cdrom from the live boot and it says that it is busy, so now i don't know what to do. . i tried it in Xfce before i restart "sudo umount /cdrom &" and it still doesn't work sorry if i seem retarded lol but im still new to all this.
 
this is the exact error message:
failed to unmount partitions 

the installer needs to commit changes to partition tables,
 but cannot do so because partitions on the following could
 not be unmounted.

/cdrom

please close any applications using these mount points.

would you like the installer to try to unmount these partitions again

                                                              go back      continue

if anyone could share some insight as to what i am doing wrong it would be greatly appreciated!

---

### Post by running_rabbit07 on 2009-08-11
> **VACSecured said:**
> i curently have xubuntu Xfce installed on my computer, and i am trying to swithch to ubuntu super OS using the program unetbootin and installing the ISO right on the hard drive. (i also tried this with mint linux and got the same error) i can get in the instalation menu and partition it, but when it starts to install i get and error that says it cannot unmount /cdrom please close all programs using it and try again. so i am no computer wiz or linux wiz for that matter, i am just getting into linux and i am still trying to learn as much as i can, but from what i do no i have tried to go into the terrminal and using the bash command "umount" mannually unmount /cdrom from the live boot and it says that it is busy, so now i don't know what to do. . i tried it in Xfce before i restart "sudo umount /cdrom &" and it still doesn't work sorry if i seem retarded lol but im still new to all this.
 
this is the exact error message:
failed to unmount partitions 

the installer needs to commit changes to partition tables,
 but cannot do so because partitions on the following could
 not be unmounted.

/cdrom

please close any applications using these mount points.

would you like the installer to try to unmount these partitions again

                                                              go back      continue

if anyone could share some insight as to what i am doing wrong it would be greatly appreciated!

You are using Unetbootin. Is there a disk in the drive? 

Does your CD drive always sound like it's turning even though there is nothing in it?

Truely sounds like there is a problem with the CD drive and not the software.

---

### Post by joe2 on 2009-08-20
> **running_rabbit07 said:**
> You are using Unetbootin. Is there a disk in the drive? 

Does your CD drive always sound like it's turning even though there is nothing in it?

Truely sounds like there is a problem with the CD drive and not the software.

I get the same problem on my netbook. I'm using a USB to SD adaptor. But in any case I believe the problem to be that unetbootin, or in my case the USB installed ISO is running with a mount point of /cdrom. Try a df from terminal, it shows on my system that /dev/sdc1 is mounted at /cdrom. /dev/sdc1 is my USB drive. BTW i don't have a CD drive on the netbook so although linux may think so there is not a hardware error to blame.

---

### Post by dilidon on 2009-09-11
> **VACSecured said:**
> 
if anyone could share some insight as to what i am doing wrong it would be greatly appreciated!

You are not doing anything wrong. Your disk where you put your installation files from the .iso file is being mounted to /cdrom, or so it seems. However, when you unmount it, the disk will continue to function and you can complete the install. Run the following command > sudo umount -l -r -f /cdrom
(Found via [http://ubuntuforums.org/showthread.php?t=1234078](http://ubuntuforums.org/showthread.php?t=1234078) from the post of iigeli). Worked for me whilst installing from a USB thumb drive.

---

### Post by Spaghetto Tortellini on 2010-04-30
I had the same problem with Lucid Lynx. However just unmounting did not work for me. Ubiquity crashed after a failed assertion.

**Fix**:
List the mounts to see the mount options your /cdrom was mounted with:
```
mount -l
```Before you start ubiquity, unmount: ```
sudo umount -l -r -f /cdrom
```Re-mount the appropriate partition with the options discovered in the first step with the mount command. Do this JUST AFTER you hit Install in Ubiquity. Please 'man mount' to see how to do this. I think the options and location will vary.

I'd recommend testing out the re-mount command once before the actual install and have it typed and ready to press return when you hit Install.

---

### Post by Chaos234 on 2010-05-01
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/313452](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/313452)

---

### Post by riseup on 2010-05-03
Hello,

I have tried to install ubuntu with a frugal install with unetbootin. Everything goes fine untill I get the error message:

Installer needs to commit changes to partition tables but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points.

I have tried to use the umount command but that didn't work. I also tried to quickly mount it again but then ubiquity still crashes. Now I don't know how to mount it again with the exact same options like the first step (mount -l). Maybe you can give me an example command? Or another solution for this problem?

I am using windows 7 to set up the boot for linux with unetbootin and an image of ubuntu 10.04. I do not have acces to a cd-rom or an usb drive, so the only possibility to install ubuntu is through my harddrive.

Greatly appreciate any help

---

### Post by irpsit on 2010-12-15
This is from my previous thread
[http://ubuntuforums.org/showthread.php?p=10241015](http://ubuntuforums.org/showthread.php?p=10241015)

I ran the frugal install from Unetbootin.

First thing, I went to the console and did sudo umount  -l -r -f  before clicking on the installer!

Then, I start the installer, choose language, then choose partitions to  install (advanced configuration). [B]This solved the error "no root file  system defined"
[/B] 
I choose a free partition as ext3 and mounted as /
And a second one choosen as swap.
The two remaining partitions were Windows (sda1) and windows recovery disk.
**This solved the error "the installer needs to commit changes to  partition tables, but cannot do so because partitions on the following  could not be unmounted /cdrom"**

Then, very important, just before I pressed "install now", I opened  again the console and typed sudo mount /dev/sda1 /cdrom (so, **this solved a fatal error that was crashing the ubuntu installation**)
And it is copying the files now! :grin:

---

