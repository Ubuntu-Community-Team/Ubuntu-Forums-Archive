---
title: "Upgrade from 9.04 to 9.10 and virtualbox install"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by texas.chef94 on 2009-11-09
SOLVED I did the upgrade which went fine then downloaded VB. See attachment.
Then went to terminal with what I thought was correct command line

allen@allen-desktop:~$ sudo dpkg -i Downloads/virtualbox-3.0_3.0.10-54097_Ubuntu_karmic_i386.deb
[sudo] password for allen: 
dpkg: error processing Downloads/virtualbox-3.0_3.0.10-54097_Ubuntu_karmic_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 Downloads/virtualbox-3.0_3.0.10-54097_Ubuntu_karmic_i386.deb
allen@allen-desktop:~$

Please advise

---

### Post by BrandonBan6 on 2009-11-09
Hello,

It looks like you are using the command:
```
Downloads/virtualbox-3.0_3.0.10-54097_Ubuntu_karmic_i386.deb
```
Which is in the Downloads directory, however your screen shot shows the .deb file on the desktop? 

You can try the following:
1.) Double click the .deb file, follow the graphical instructions

2.) Change the terminal command to: 
```

cd /Desktop
sudo dpkg -i virtualbox-3.0_3.0.10-54097_Ubuntu_karmic_i386.deb
```

---

### Post by MelDJ on 2009-11-09
just double clicking the package and then installing it is much easier

---

### Post by texas.chef94 on 2009-11-09
> **BrandonBan6 said:**
> Hello,

It looks like you are using the command:
```
Downloads/virtualbox-3.0_3.0.10-54097_Ubuntu_karmic_i386.deb
```
Which is in the Downloads directory, however your screen shot shows the .deb file on the desktop? 

You can try the following:
1.) Double click the .deb file, follow the graphical instructions

2.) Change the terminal command to: 
```

cd /Desktop
sudo dpkg -i virtualbox-3.0_3.0.10-54097_Ubuntu_karmic_i386.deb
```

This is just informational. I am in and the unit that this Ubuntu in question is indeed a 64AMD and that was the VB version I downloaded. It seems the 64 AMD was not being recognized (Makes no sense to me) but I downloaded the version as if this was a 32 bit and worked like a charm. Thanks

---

### Post by BrandonBan6 on 2009-11-09
Great! Thx for the update, can you mark the thread as solved? 

Have a great week!

---

