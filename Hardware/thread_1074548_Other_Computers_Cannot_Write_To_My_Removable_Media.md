---
title: "Other Computers Cannot Write To My Removable Media"
date: 2009-02-19
forum: Hardware
---

### Post by Flactivist on 2009-02-19
Hi,

In the last few months I've found that when I plug removable media into the computers of my colleagues they lack permission to add files. In both cases their computers were Mac OS X laptops.

I'm running Ubuntu 8.10

Last night I brought my Seagate external drive to a friend so he could load some video files onto it. I can connect to the drive via USB or Firewire, depending on which is convenient. We plugged his Mac Powerbook in via USB, the drive mounted and he could read files, but lacked permissions to add files. This drive is formatted as NTFS.

Up to this point I had not performed any permissions commands on the drive. I plugged the drive into my Ubuntu laptop and opened the drive folder in Media as root. I opened up the permissions and when I tried to change the group permissions it automatically reverted back to root. The permissions screen *says* that "Other" users should have read and write permissions.

A couple months ago I plugged my usb stick into a colleague's laptop to transfer files and she also did not have permission to write. I didn't have time to look into it then but it appears related. The USB stick is formatted as vFAT (FAT 16).

I've searched for help on this issue but I only find posts by users who cannot write to drives from their own machines, not other machines. I don't think I had this problem before upgrading to Ubuntu 8.10. Thanks for your help!

---

### Post by geraldm on 2009-02-19
>The permissions screen *says* that "Other" users should have read and write permissions.
Regardless of what the screen says, NEVER change the permissions of "other" to allow read/write unless that is *exactly* what you want to do.
You can use the command "ls -l " + the mount point to show the user and group permissions.  
It is possible to read/write from any filesystem that allows it.
You may need to learn how to mount, and how to change permissions.
The thread title suggests that you are new and learning; but it is simply false.

best regards,
Gerald

---

### Post by Flactivist on 2009-02-21
Hi Gerald,

I appreciate the advice and the correction. I've been using external drives and USB sticks for about 10 years now and this is the first time I've plugged an external drive into another person's computer and they don't have write permissions to my drive. I'd appreciate any advice you have addressing that ongoing behavior. Thanks.

---

### Post by Flactivist on 2009-02-21
After more research I'm thinking this is a problem of Mac OS X being unable to write to NTFS.

---

