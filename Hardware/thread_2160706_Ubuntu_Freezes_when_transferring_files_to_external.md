---
title: "Ubuntu Freezes when transferring files to external hdd"
date: 2013-07-07
forum: Hardware
---

### Post by Elliander on 2013-07-07
I am using a  TB SATA hard drive with 512 byte sector size with two partitions set to FAT32. The entire drive is using a Hybrid MBR/GPT which worked perfectly in Windows 7 . That is, until I made it a Hybrid. I need it to be a Hybrid because I need to use this drive with legacy hardware that requires both MBR and 512 byte sector sizes. I am currently using it with a Plugable U3 USB 2.0 Docking Station (the only enclosure I could find that will support larger hard drives and still present it as a 512 byte drive). I had to format it in Windows 7 because gparted won't work with it at all.

I need to copy 1 TB of data from one USB hard drive to another, and so far I am not having the best of luck with it. In small chunks everything is fine, but if I tell it to copy even 100 GB at once what eventually happens is that the computer goes into a power saving mode and then it just stops transferring files to it. Instead, the 
"Time Remaining" estimate gets longer and longer. Eventually the drives becomes inaccessible and then the whole system locks up until I shut off the drive. Then everything works and when I turn it back on it all works again. When I went into system > preferences > power management I found that suspend mode was already turned off, but also turned off the monitor and I still have the problem so whatever is happening isn't related to power management options.

Copying files from either external hard drive to the computer is faster than from one to the other and doesn't appear to cause any problems, but when I then transfer files from the internal hard drive to either external I have the same problem again.

As a related issue, one of the folders had 23.5 GB of data copied (out of 100) before everything froze and I had to shut it off. Now the folder cannot be accessed and when I attempt to delete it I get an I/O error, but I can easily copy and delete other files to it. 

EDIT: Now I can't seem to add any files to that partition at all. It says it's a real only file system now :( The hard drive itself has no bad sectors, and have already run a full surface scan that took me 46 hours.

Operating system is Ubuntu 7.10 64-bit. Attempted in both a dedicated Ubuntu desktop and also within VMware in my Windows 7 laptop. Same problems.

P.S. > Please don't tell me to simply "upgrade to the latest distro" because I have tried it and didn't like it. In fact, I hated 12.10 so much that I ended up wiping a hard drive to get rid of it and reinstalled 7.10. Within VMware I did try 12.10 again, but it can't even see Windows 7 and even there it freezes almost all the time. The user interface is so different that as far as I am concerned 12.10 is to 7.10 as Mac is to Windows. The side bar never goes away, the menus don't make sense, and there is no terminal to be found. I will never again use any distro that uses the same UI as 12.10.

---

