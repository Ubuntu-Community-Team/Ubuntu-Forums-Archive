---
title: "Resize Windows for Ubuntu and reboot GRUB Error 17"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by flylehe on 2009-03-04
Hi,
I am reinstalling my Ubuntu on my laptop with Windows XP existing. 

First, with Partition Magic, I resized my Windows C (system) disk to free some space in order to add into new Ubuntu's root. To complete the partition, I have to reboot but at the very beginning of restart I got an error "GRUB Loading stage 1.5 GRUB loading, please wait... Error 17" and it became stuck there. 

I then have no idea how to fix it and I start reinstalling Ubuntun from cd. At the partiton part, the installation guide at first did not recognize the size changing of Windows C but later report the size is smaller that what it shows. It lets me either ignore or cancel. I cancelled and restart again without CD. Now same error of GRUB Error 17 happen again. 

Really appreciated if someone could help me out! Thanks in advance!

---

### Post by ajmorris on 2009-03-05
hi there,
a grub error 17 is nothing to be concerned about. It is simply that GRUB cannot match its present knowledge of a disk structure with the new one it has found. Why you are getting the error after a simple windows NTFS partition resize, i do not know. 
However, a simple re-install of grub into the MBR should solve this... (if you installed grub into a partition and not the mbr, please dis-regard this, and tell me that is what you have done :) )
run the following steps from your ubuntu live cd to re-install grub:
```
sudo grub
```
```
find /boot/grub/stage1
```
```
root (hd#,#)
``` (where #,# are the numbers that the second step gives you)
```
setup (hd0)
```
```
quit
```
```
sudo reboot
```


AJ

---

