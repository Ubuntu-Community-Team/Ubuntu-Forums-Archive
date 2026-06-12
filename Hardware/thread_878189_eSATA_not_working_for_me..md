---
title: "eSATA not working for me."
date: 2008-08-02
forum: Hardware
---

### Post by rmjohnson144 on 2008-08-02
I tried to get my eSATA 500GB drive working, but it seems to just refuse to work.

First try, it said there was an eSATA drive and when I clicked on it, it asked for a password to set it up.  It then said afterwards that it was unable to mount the device and the details said, "fuse:mount failed: device or resource busy"

second, I boot back into Vista Ultimate x64 and backup the eSATA and then reformat without issue.  I boot back into ubuntu and it lists the drive and I get the same error again.

I have the drive formatted with NTFS.  I tried to use FAT32, but couldn't as it is limited to 32GB.  I tried several programs to do it and they all refused to run under vista x64.  I even tried UBCD and the western digital tools couldn't find the drive.

I think it may be an eSATA issue, but not sure as the FAT32 was for IDE drives and the old format without the 32GB limit is for win98.

Thanks for any help
-=Mark=-

---

### Post by rmjohnson144 on 2008-08-02
well, it's getting much worse now.  Not only did I lose my backup, but killed my RAID5 disk that had vista installed on it.

now, after I have installed Vista once again, I have decided to delete the drive's partitions so it is like brand new with no file system all.  I get into Ubuntu and it doesn't show up of course, but now I can't find a way to setup my disk and format it.  I see no Windows equivalent to,"Computer Management" to accomplish this.

Anyone know of a program to let me setup and install a new hard drive for Ubuntu.
-=Mark=-
PS. sorry for the newbish questions, but search hasn't been very friendly to me.

---

### Post by rmjohnson144 on 2008-08-02
OK, after running gparted and failing at installing the drive I see in the gparted menu a /dev/mapper/sil_aiahaecbacff that is assigned to my 500GB drive as well.  Could this be interfering with the /dev/sde from installing properly?

Not sure what else to do at this point.

also, is there a format utility to format in fat32 in linux?  I found the document on installing a new drive, but it only gives a way to format an ext3 partition.

-=Mark=-

---

### Post by cdtech on 2008-08-03
You can create an MS-DOS/Windows XP file system under Linux, enter:
```
sudo mkfs.vfat /dev/sdc1
```

"sdc1" being your device of course.........

---

### Post by rmjohnson144 on 2008-08-03
> **cdtech said:**
> You can create an MS-DOS/Windows XP file system under Linux, enter:
```
sudo mkfs.vfat /dev/sdc1
```

"sdc1" being your device of course.........

dang, it almost did it.  I went and closed gparted before trying so it wouldn't interfere with mkfs and it said I wasn't done or some such.  I closed gparted anyway and went back in and looked around and seen a bland area with a pull-down menu arrow and sure enough there was an apply option that I hadn't been using.  So I explored the menus again to see if I overlooked anything and sure enough there was a format option menu and I selected FAT32 and hit apply and it set it all up.  

I still wasn't sure it formatted because it went by so quick so I thought I'd reboot and see if Ubuntu would auto-pickup the drive.  well it got hung up at DMRAID or something that I was running before trying this 500GB drive.  I have a dual boot system and was trying to use my Intel RAID in Ubuntu, but I could figure it out or find a good article on how to do it.  

I found by going back into Vista and either formatting it to NTFS (which was its original mode when Ubuntu set it up) or just plain deleting the partion completely, then it wouldn't get stuck on the dmraid and boot right into windows.  I tried EXT3, FAT32 both and they both get stuck at dmraid every time.

anyway, now I need to know how to remove DMRAID.  I remember running it the first time that it asked to install it, and I clicked yes, but it never worked for me nor did I pursue getting it to work as it was getting very complicated and from the looks of it, I'd lose my Vista RAID if I tried to configue the Linux fakeraid.

Thanks tremendously for the help
-=Mark=-

---

### Post by rmjohnson144 on 2008-08-03
OK, I just noticed when trying to access the drive that now is saying that,"You are not privileged to mount the volume 'eSATA'."  But it is not asking for a password or anything to allow me privileges this time.

Next, I go to "Computer" and right-click and select properties and under the properties tab I get,"The prmissions of "eSATA" could not be determined."

grrr. this is driving me nuts.  every time I move one step forwards, I end up moving two steps back. and of course it never follows the path of the documentation.

-=Mark=-

---

### Post by rmjohnson144 on 2008-08-04
OK, I just decided to undo my Vista raid and and enabled AHCI then just do my windows quick fix and just reinstall the OS.  So, after reinstalling Ubuntu on one of the AHCI drives (My current Ubuntu is on my JMicron controller) now I can access all my drives without issues. 

I switch back to my JMocron drive and startup this Ubuntu I can find the new Ubuntu drive but still can't access my eSATA drive.  

so, I guess maybe if I uninstall my current eSATA and reboot, then maybe Ubuntu can reinstall it and have it work.  I find it strange it doesn't work at all on this installation at all, but the other install finds it just fine.  The only difference was it wasn't plugged in during the install on this drive, but was on during the new AHCI install.

-=Mark=-
PS.  Is there an easy way to get rid of the GRUB menu that the AHCI installed.  It found this drive even though I had it switched in the BIOS to boot from the other drive.  I'm so so sorry for asking such a seemingly simple question, but I am just extrememly wore out from reading tons of documents/google searches/message posts that my brain has all but melted away!

---

