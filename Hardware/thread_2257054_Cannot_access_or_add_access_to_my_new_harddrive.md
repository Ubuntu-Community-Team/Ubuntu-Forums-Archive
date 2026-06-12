---
title: "Cannot access or add access to my new harddrive"
date: 2014-12-16
forum: Hardware
---

### Post by robinuitdetoekomst on 2014-12-16
Hi,
So i have a server with (i think the latest version of) ubuntu installed on it. I have 6*1TB drives and 2*64GB SSD drives. I have 16 GB of ram and a quadcore processor (if you want to know which one let me know). 1 of my 1TB drives is used for the OS (i know i should have used the SSD for the OS i just didnt know there where ssds in it when i bought it). I followed this tutorial: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
To install my other hard drives. Now i got to the part where it says: If you want to allow a normal user to create files on this drive.... But unfortunatly when i enter this in the terminal and press enter:
sudo chgrp plugdev /media/mynewdrive

I get the following error (its in dutch so ill translate it in english):
Changeing of group from &#8216;/media/mynewdrive&#8217;: Edit not allowed
Here in dutch:
Veranderen van de groep van &#8216;/media/mynewdrive&#8217;: Bewerking niet toegestaan

I already added a partition to my drives and i know i need different mounting paths. All these
hard drives are FAT32.

Please help i need these drives because i want to make a file server to store important files.
Any help is welcome, but please if you have the same problem dont come here and post something like
"I have the same problem"
I dont need to know that i just want to know how to fix it :p.

If you need more information let me know what.

---

### Post by robinuitdetoekomst on 2014-12-16
Ok never mind noone helped but i found myself. If someone wants to know how i did it:
[http://askubuntu.com/questions/74806/how-can-i-change-permissions-on-external-drives](http://askubuntu.com/questions/74806/how-can-i-change-permissions-on-external-drives)

---

