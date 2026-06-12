---
title: "Mounting"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by penguinchrissy on 2006-07-17
I've been having a lot of trouble mounting antyhing on ubuntu. Right now I have a hard drive that I have partitioned into two parts both parts are NTFS that I'm trying to gain at least read acess to I would also like to beable to delete files from them.(I know its risky but I'm going to format them any way). I also have to usb drives that I'm trying to mount. A thumb drive and a protable hard drive. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb5 /media/hdb5 ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /media/hdb1 ntfs nls=utf8,umask=0222 0 0

that is my fstab. My computer recongizes that the thumb drive is there but wont' let me mount I can access hdb5 but it won't let me access hdb1. Anything will help. Thanks in advance.

---

### Post by wahman143 on 2006-07-17
1.How are you attempting to mount your usb drive?  What command sequence?

2.What is the error message coming back when you try to mount that NTFS drive?  What command sequence are you using to try to mount it?

W.

---

### Post by penguinchrissy on 2006-07-19
The mounting of the NTFS is now working I restarted and it was mounted properly. I'm not trying to do anything with the USB drive I'm just trying to plug it in and then let its be discoverd. When it is reconigzed and I try and right click mount it it says it can't be mounted.

---

### Post by wahman143 on 2006-07-19
> **penguinchrissy said:**
> When it is reconigzed and I try and right click mount it it says it can't be mounted.
Is there a specific error or does it just deny you?

---

