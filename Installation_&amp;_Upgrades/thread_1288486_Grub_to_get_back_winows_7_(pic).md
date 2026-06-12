---
title: "Grub to get back winows 7 (pic)"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by Morty007 on 2009-10-11
Scenario-Originally dual booting vista and ubuntu. I now installed windows 7 on top of vista, so now no grub. I've seen different grub instructions here, but not sure which one to go with.

What do I do to get back grub with options for windows 7 and ubuntu? 


[[img]http://xs844.xs.to/xs844/09410/disk369.png[/img]](http://xs.to)

---

### Post by bulldog on 2009-10-11
Hi Morty007,
Try this if you have a live cd on hand:

This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.


Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by Morty007 on 2009-10-11
Wow, thanks for the quick reply. Gonna try it now.:guitar:

---

### Post by Morty007 on 2009-10-11
Bulldog-Worked like a charm. I noticed now that it says Windows vista (loader) instead of Windows 7, but that's ok. Thanks again.

---

