---
title: "Can't use the second Hard Drive"
date: 2009-10-17
forum: Hardware
---

### Post by Mahoney88 on 2009-10-17
Hi all:

I've installed Ubuntu 9.04 and all went well except for being able to access the second hard drive. I formatted the 2nd drive with Gparted to ext3 and that went well.
The drive shows up in the Places drop down ( where it should ) but when clicked on all it does is bring up Nautilus and I'm unable to use the drive. The drive is listed ( mounted ? ) in the media directory/folder - which from what I understand is where it should be. But when the drive is clicked on, the right pane just shows a folder called: "lost and found" which is empty. 
So, what's missing OR what am I missing??
 

 PS, is there any kind of “disc utility” program for Ubuntu or Linux besides Gparted, which is only for formatting.

Thanks in advance to those that answer,

M

---

### Post by oldfred on 2009-10-17
In synaptic is a storage device manager which provides a gui for mounting and editing fstab. PySDM is a PyGTK Storage Device Manager.

You need to create directories and mount them. You also give permissions on who can access since linux is a mutiuser system. Usually you just want yourself to have access.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
# see above for labeling & mounting & permissions
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

