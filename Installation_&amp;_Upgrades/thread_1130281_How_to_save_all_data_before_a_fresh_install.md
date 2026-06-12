---
title: "How to save all data before a fresh install?"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by WE0H on 2009-04-19
I would like to upgrade to the 9.04 version. I run 8.10 now. How do I save all emails & settings in Thunderbird, bookmarks in Firefox & all personal files that I have collected over the years? All I want is a fresh 9.04 install and to have my email, browser settings, and personal files saved to move over to the new 9.04 install. I only have a year experience on Linux so I am basically a newbie...LOL...

I have an external USB drive to move files onto.

Many thanks,
Mike

---

### Post by Svensk023 on 2009-04-19
well you will want to back up everything in your home folder.

But it avoid this nuisance, when you are partitioning your HDD on your Jaunty install. make sure to separate your primary partitions so that one is mounted at "/" and the other (with the majority of your HDD space) mounted at "/home" that way if you ever need to fresh install again, you will be able to save all your personal files and settings.

so for example if i had a 300Gb HDD, this is how id slice it up

Linux-Swap (make this twice the size of your RAM) so if you had 1Gb RAM make it a 2Gb Swap partition.
Primary ext4 (yay its supported in Jaunty!) mounted at /  make this about 30-50Gb
Primary ext4 mounted /home  give this the rest of your HDD space.

thats how I have my setup. There are other setups people use, but this one always suffices for me.

---

### Post by ales on 2009-04-19
> **WE0H said:**
> I would like to upgrade to the 9.04 version. I run 8.10 now. How do I save all emails & settings in Thunderbird, bookmarks in Firefox & all personal files that I have collected over the years? All I want is a fresh 9.04 install and to have my email, browser settings, and personal files saved to move over to the new 9.04 install. I only have a year experience on Linux so I am basically a newbie...LOL...

Many thanks,
Mike


Hello,

you need to make a copy of the mail folder from thunderbird. Just right click in the Thunderbird at your folder name /Local Folders or whatever you named it/ and then click in the menu on Server Settings. You can find there the path to the Local storage. From there you have to copy all files. After fresh install, you just copy it back to fresh Thunderbitd installation. As for the Firefox, I don't know, never tried to save the bookmarks, but I suppose will be very similar to Thunderbird.

---

### Post by WE0H on 2009-04-19
Wow you guys are fast to reply. Cool. Thank you!!!

Question on getting rid of all old data on the HD, should I run a Kill Disk on the drive after I archive my files and setting files or will Ubuntu clean the drive of all low & high level files when it does it's partitioning? I have run into old boot loaders when doing Winblows installs and found running a Kill Disk program, to write all ones to the drive, will eliminate all old data, boot loaders and so forth.

Mike

---

### Post by ales on 2009-04-19
> **WE0H said:**
> Wow you guys are fast to reply. Cool. Thank you!!!

Question on getting rid of all old data on the HD, should I run a Kill Disk on the drive after I archive my files and setting files or will Ubuntu clean the drive of all low & high level files when it does it's partitioning? I have run into old boot loaders when doing Winblows installs and found running a Kill Disk program, to write all ones to the drive, will eliminate all old data, boot loaders and so forth.

Mike


As I remember, when I did fresh install of a newer version, Ubuntu cleans all data regarding the system, also all data on the disk where it is going to be installed. But when doing a fresh install you can create and delete  partitions so u can basicaly format it and so the disk will be clean.

Ales

---

