---
title: "External drive will not give permission to write or read"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by wdriver on 2008-02-23
I have mounted an external drive using gparted, formatted to ext3. It is recognized by the system with desktop icon, but when I attempt to write a file or folder to the drive, I receive a access denied notice stating I do not have permission to access the drive. How do I correct this. I plan to use the drive for storage. Do I need to reformat? Repartition?

Thanks

---

### Post by taurus on 2008-02-23
You just need to change the mount point for that drive from root to your login name.  _Assuming_ it is mounted to /media/storage and your login name is **wdriver**, open a terminal and run

```
sudo chown -R **wdriver**:**wdriver** /media/storage
ls -la /media
```

---

### Post by davidryderuk on 2008-02-23
Hi, I read on another part of the forum that you can type "gksudo nautilus" into the terminal and that will open up a window in /root. If you then navigate to /media in the window you should be able to right click on your hard drive and go to properties where there is a tab for changing permissions. 

The window essentially gives you administrative user rights. I believe that parts of the computer other than the home folder are locked down by default in Linux for security reasons.

Hope you get your hard drive sorted.

---

### Post by wdriver on 2008-02-23
Thanks for your help. It is much appreciated.

---

### Post by wdriver on 2008-02-23
Thanks for your assistance. Much appreciated.

---

### Post by iamaqbot on 2008-02-25
Thank you for this. This cleared about a week of frustration and me questioning my hard drive purchase.

---

