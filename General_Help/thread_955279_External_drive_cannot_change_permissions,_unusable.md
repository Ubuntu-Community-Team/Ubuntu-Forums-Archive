---
title: "External drive cannot change permissions, unusable"
date: 2008-10-22
forum: General Help
---

### Post by skippy2222 on 2008-10-22
hello, please can somebody help me, 

I have a 300GB external hard disk connected to my laptop running 8.04, this works fine, I can read, write and modify no problem, filesystem is fat32, the owner is set as root.

I have a secondary external device, a 400gb media drive, again filesystem is fat32, however i cannot do much here as everything is locked, owner set as my username.

how can I get this drive to operate as it did under windows allowing me to read write and modify, can it be set fo this each time it is hot plugged?

thanks in advance

---

### Post by skippy2222 on 2008-10-22
any attempt to copy or cut and paste data here results in Error setting owner: Read-only file system error

---

### Post by scouser73 on 2008-10-22
Hi Skippy, what you need to do it to open up terminal and enter the command **gksudo nautilus** this will give you access as the Root user, make your way to your drive, **right click**, select the **Permissions** tab and change your permissions, remember to click **Apply Permissions To Enclosed Files**

---

### Post by sacauntos on 2008-10-22
Hi, I had the same problem with a 160 GB iomega USB hard drive. I must warn you that I am by no means an expert, but I'll tell you what I did. 

First I changed ownership of the drive with chown and permissions with chmod in a terminal and, strangely, my drive would work for a couple of accesses to it and then it returned the same error you had.

So I decided to reformat the HD to ntfs (and as I tell you I'm not an expert, and as the drive was unusable in linux, I had to do it in WinXP).

After that, I still had to chown and chmod permissions in ubuntu, but it started working from then on, both in windows and in ubuntu.

There is only one thing that maybe someone can solve for me. As long as I try to delete a file from the USB HD, a warning message pops up saying that 

> "it was unable to move the file to the trash bin, do you want to delete it permanently?"

Summarizing, the drive works ok, but there is this little nuisance that I won't mind to have fixed! Also, does someone know a way to have dealt with formatting a drive that is detected as Read-only?

Cheers

---

