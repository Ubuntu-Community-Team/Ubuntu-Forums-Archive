---
title: "Is there a way to back up everything?"
date: 2008-11-16
forum: General Help
---

### Post by kh1116 on 2008-11-16
I want to reinstall windows to dual boot and the only way for me to do this is to install windows first by formatting (windows installer doesnt detect my partitions). If i back up all of my home folder, will it keep all of my program settings, etc? also is there a way to keep all of the programs i have installed or should i just back up my home folder?

---

### Post by cariboo on 2008-11-16
You can back up your hard drive using something like partimage, but I would just back up your home directory and do a clean install.

Jim

---

### Post by drs305 on 2008-11-16
You can create a list of installed apps with the following command, which will be saved as package-list on your desktop. It will allow you to import your current installed apps into your new setup. 

It will not restore your user settings. To do that, you can make an image of your partitions with partimage, which will restore the partition exactly as it was when you copied it.

To create a list of installed packages:
```
sudo dpkg --get-selections | grep -v "deinstall" >~/Desktop/package-list 
```
Make sure you copy the file to a partition/device you won't be formatting!

To install the same apps, copy the file package-list to your new Desktop, then run:
```


sudo aptitude update
sudo dpkg --set-selections <~/Desktop/package-list
sudo apt-get update
sudo apt-get upgrade

```

---

