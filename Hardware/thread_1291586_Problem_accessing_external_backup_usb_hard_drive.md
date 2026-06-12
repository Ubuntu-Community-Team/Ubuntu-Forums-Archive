---
title: "Problem accessing external backup usb hard drive"
date: 2009-10-14
forum: Hardware
---

### Post by starcow on 2009-10-14
I was running ubuntu 9.04 on my acer aspire one, and backed up /home/ to an external ext4 hard drive manually (copy and paste)

I accidentally used dd and overwrote my harddrive.
I now need to access my external hard drive to restore my backed up files, however when i attempt to access my home directory /home/daniel on the external hard drive, it informs me that i do not have  permission to access this folder.

I have everything from my computer on that drive, and i have no other backups and i cannot access it.. this is bad.

I have tried accessing it from a couple different distros and live usbs, ive tried accessing with ext2fs on my windows laptop but to no avail. I dont know whether that is because it is ext4 or protected, im not sure which, but it displays the folders as 0bytes with no contents.

I even tried to reinstall ubuntu, and mount the external hd as my /home with exactly the same user and password, but with no luck, the installer crashes after copying files, when trying to set up the user home directory.

I am open to any suggestions at all at this point. I am not afraid of the command line. Let me know if any more information is necessary, thanks a ton in advance!

---

### Post by Dark_Stang on 2009-10-14
Sounds like a permissions issue. Run "sudo nautilus" to open up a file browser with root permission. See if you can view your files that way.

---

### Post by starcow on 2009-10-15
That worked!
I cant believe I didn't try that, thanks a ton.

---

