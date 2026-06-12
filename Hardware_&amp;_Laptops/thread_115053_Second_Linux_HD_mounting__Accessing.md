---
title: "Second Linux HD mounting?  Accessing?"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by interse on 2006-01-09
I just added a second hard drive, previously used, and formatted in Linux.  In Disks Manager it shows up as follows:
    Device:               /dev/hdb1
    Filesystem:         Extended 3
    Access Path:       none
    Size:                   36.89 GiB (Free space not available)
    Status:               Inaccessible
                                  ENABLE                                   BROWSE
                           active button, but does nothing     not active

     Partition 1
     Swap Partition


As I said, this drive was previously formatted by Kbuntu (?).  Doesn't matter.  If and when I can access partition 1, I will remove all of the files and then use this drive for backup storage.  This is all I wish to do.

My  /etc/fstab   static file system information is as follows:

   /dev/hda1   /         ext3   defaults, errors=remount-ro 0     1
   /dev/hda5   none  swap   sw     0  0
   /dev/hdc     /media/cdrom()  udf,iso9660 ro,user,noauto  0   0
   /dev/fd0      /media/floppy0   auto  rw,uswer,noauto  0   0


WHAT DO I DO TO MADE hdb ACCESSIBLE.   Is it as easy as adding a few lines, repeating e.g.   /dev/hdb1  /    ext3    ETC.
      AND            /dev/hda5  /    swap    ETC.

IS THIS ALL THAT I WOULD NEED TO DO?

---

### Post by aysiu on 2006-01-09
```
sudo cp /etc/fstab /etc/fstab_backup
sudo mkdir /second_drive
sudo gedit /etc/fstab
``` Replace all text with this ```
/dev/hda1 / ext3 defaults, errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom() udf,iso9660 ro,user,noauto 0 0
**/dev/hdb1 /second_drive defaults**
/dev/fd0 /media/floppy0 auto rw,uswer,noauto 0 0
``` Save
```
sudo chmod -R 777 /second_drive
```

---

### Post by interse on 2006-01-09
/dev/hdb1 /second_drive defaults

Is the above line what I actually insert into fstab or are you indicating that I should insert the following:
    /dev/hdb1/ ext3 defaults, errors=remount-ro 0 1
    /dev/hdb5/ swap sw 0 0

If your instruction is to insert " /dev/hdb1/second_drive defaults "  then, because I do want to learn, what is it that I am indicating.   Why would I not list the two lines that are copies of the hda lines with hdb substituted.  Sorry for the follow-up, but I am just trying to understand what is going on.

Thanks for clarifying this for me.  I do not just want to copy something w/o understanding why.

---

### Post by aysiu on 2006-01-09
Actually, I wanted your to replace your entire /etc/fstab with what I posted. Note, though, that the first command I gave you made a backup copy of your /etc/fstab.

For more on understanding the fstab...
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by interse on 2006-01-09
Thanks for the help and the follow-up explanation, as well as the reference link.  I am sure that others will benefit from your help, as well.

When I searched the threads I found a great deal of information on 2nd drives with FAT32 and/or NTFS, nothing on my rather straightforward question.

Thank you again.

---

### Post by interse on 2006-01-10
I followed all of the instructions from Aysiu.  Still Disk Manager shows hdb1 as being inaccessible, Size: 36.89 GiB (Free space not available) and Status: Inaccessible.

I am still having some difficulty with the idea of mounting, but I suspect that I have to mount hdb1 in order to access it?  Is this correct?  How would this be done?  

Also in the line to be added to /etc/fstab:
    /dev/hdb1 /second_drive defaults

   shouldn't I have also added   ext 3    before    defaults   ?

I realize now that while I thought I had left Windows, the patterns established in accessing hard drives have not left me: this would account for my current difficulty with hdb, I suspect.

---

### Post by aysiu on 2006-01-10
[QUOTE=interse]
Also in the line to be added to /etc/fstab:
    /dev/hdb1 /second_drive defaults

   shouldn't I have also added   ext 3    before    defaults   ?[/QUOTE] You're so right. I left that off, and it's important!

---

### Post by interse on 2006-01-10
Bingo!   As you said, it was important.  
 
I now can Activate hdb1 in Disks Manager and I can Browze which opens  second_drive - File Browser.  From here I can copy, delete, paste, etc.

   (Yes, I am still GUI dependent, though not entirely)

Is there any other way to browze hdb1, such as from the Places menu?  I have tried and so far I have not been able to 'see' hdb1 from any of the options in the Places Menu.  Perhaps I need to look further and deeper.

Thank you again for your help and especially for the links which have added much to my learning Linux.

---

### Post by interse on 2006-01-10
Is there any other way to browze hdb1, such as from the Places menu?  I have tried and so far I have not been able to 'see' hdb1 from any of the options in the Places Menu.  Perhaps I need to look further and deeper.

---

