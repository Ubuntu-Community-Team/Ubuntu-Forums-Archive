---
title: "Triple boot - Triple Drives"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by Guns90 on 2009-03-10
A friend just bought a new computer and was going to trash his old one, so I snatched the SATA drive.
I now have three drives and I'm currently dual booting Vista on sda1 (kids demand it for school) and Ubuntu on sdb1. I want to install some other linux distros on sdc1, one at a time, just to play with them and see what they are like.  

I know simply by using it before that GRUB installs a second distro anywhere you want it and allows you to choose which one you want to boot in to. My questions are...will GRUB allow me to install another distro on sdc1 the same way with the same kind of results booting into them? If not, what do I need to do?  If so, what will I have to do should I choose to just not use sdc1 in the future and return to dual booting?  Thanks

---

### Post by upchucky on 2009-03-10
all that is involved is editing the menu.lst file when changing/adding/removing drives.

put new drive in the system then download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh
```

then you just need to enter the drive parameters to the menu.lst

---

