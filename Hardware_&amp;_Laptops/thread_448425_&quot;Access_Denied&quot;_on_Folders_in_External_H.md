---
title: "&quot;Access Denied&quot; on Folders in External Harddrive"
date: 2007-05-19
forum: Hardware &amp; Laptops
---

### Post by NicolaiM on 2007-05-19
This is my recent odyssey of having a series of problems on Kubuntu. (I guess it never rains but it pours)
The present problem will be at the end of the post. Since I could find no proper way to explain my situation without a little backstory, some of the post might seem redundant. You can probably skip over the first part.


---------------------------------- Backstory

Yesterday I discovered that my laptop couldn't start Kubuntu because of some problem with the the system. Apparently I hadn't installed kdm, which I didn't even bother checking.

Instead of trying to fix the problem by reconfiguring the existing system, I instead put my install-CD in the drive and rebooted. The plan was to copy all important data to my recently (same day) bought external harddrive.

This external harddisk is not meant to be used by any Windows-computers, so I figured the best option would be to format the drive in ext3 to make sure there was no possibility of data-loss. I opened QTParted and it formattet succesfully.

Now the problem was that the drive was not mountable by the user. I had the same problem with the internal harddisk, so I opened both fstab and the disk configuration in System Settings. I couldn't get the external harddrive to obtain write access for a normal user (root only), but somehow I managed to get it done on my desktop.

I copied (and moved!) a lot of data from my desktop-computer to the external harddrive, because I felt it had to be done at some point.

When I connected the external harddrive to my laptop, It had thankfully kept the write-access, but only to the external drive, not to the data from my desktop. I figured It was easier to deal with this from my desktop, so I just made a folder on the external harddrive and threw everything from my laptop into it.

From my desktop i could see the problem was that the overall folder was root, allowing write access for users, the content was on the other hand owned by the respective uploading user. Because I had used the live-cd, this meant that user "Ubuntu (999)" would not let user "Nicolai (1000)" write in some folders, and vice versa.


---------------------------------- Direct reason for problem

With help from a site that I cannot find at the moment (I believe it was at Ubuntu documentation) I managed to get folders writable using 

| sudo chmod 667 'media/external'

The problem was there is a lot of subdirectories, so I would have to keep at this. Not being native in English I saw the --recursive command and thought it meant the same changes would be done on the subdirectories.

| sudo chmod 667 --recursive '/media/Ekstern'

Instead of fixing the problem, it did the equivalent of unchecking the "get access to" under advanced settings in the "folder permissions" tab. (I read these options in my own locale (dk), so these names are just guesses)



---------------------------------- This is where I'm at now.

I now have folders and subdirectories with different access priorities. At the same time a large section of my data belongs to the user "ubuntu (999)", which means I have no easy (graphical) way of changing the permissions for the folders. Simply speaking my drive is one giant mess.

I would like to know how to change ownership to "nicolai (1000)" and an easy way to make all data read/write/access capable.



Any help would be highly appreciated.
NicolaiM

---

### Post by lw5 on 2007-05-19
are you looking for something like this:

sudo chown nicolai -R * (change ownership of all files and folders to nicolai)
sudo ch**mod** 777 -R * (allow read, write execute on all files and folders by everybody)

Otherwise your problem might ly in how you are mounting your external drive. Search for fstab, mounting and permissions.

---

### Post by NicolaiM on 2007-05-19
> **lw5 said:**
> are you looking for something like this:

sudo chown nicolai -R * (change ownership of all files and folders to nicolai)
sudo chown 777 -R * (allow read, write execute on all files and folders by everybody)

Otherwise your problem might ly in how you are mounting your external drive. Search for fstab, mounting and permissions.


Yes. iarwain_  in the #kubuntu channel helped me get it fixed, but otherwise thank you. My problem was that I thought the appropriate command was "chmod 666" instead of 777. I had also accidentally changed permissions  and ownership for the "lost+found" folder, which complicated matters.  


I used chmod 777 instead of chown 777. Is there any important difference I should know about?

---

### Post by lw5 on 2007-05-20
No I made a mistake as a result of our copy-paste-society, it should be **chmod**.

---

