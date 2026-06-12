---
title: "Communicaiton between Isolinux and Windows"
date: 2010-02-01
forum: Hardware
---

### Post by Corinthians on 2010-02-01
What I'm trying to do is install Ubuntu onto a jump drive and then have some way for the Ubuntu install to communicate with Windows on a single jump drive.

I first tried partitioning the drive into one fat32 partition and one reiserfs partition.  But if I made the first partition fat32 then it wouldn't boot and If I made the reiserfs first then windows wouldn't recognize the fat32 partition.

And so I reformatted the whole thing tried the USB startup Disk Creator.  With that I can read the drive in Windows and Boot into Ubuntu but there's no way to communicate between the two.

I found a tutorial ([link]("http://www.pendrivelinux.com/sharing-files-between-ubuntu-flash-drive-and-windows/")) for how to share data between Ubuntu and Windows but I couldn't get it to work and some of my filenames are different. (isolinux instead of syslinux and initrd.lz instead of initrd.gz)  Also when I try and and change the permissions of the files to read and write it won't let me even using sudo.

So if one of you could help me either convert the tutorial to work with my install of linux or show me how to install it so that It'll work with the tutorial or just get my original idea to work in general that would be amazing!

I'm still fairly new to linux so I'm fairly certain it's something I'm doing wrong. Also I'm using an 8gb jump drive and Ubuntu 9.10.

---

