---
title: "why the partitons still have ntfs3g,,can i remove it"
date: 2011-08-26
forum: Hardware
---

### Post by zissshh on 2011-08-26
why does the partitions have NTfs3g,,with them,,,and how do i remove them and i have lot of input output errors on my hard disk and usbs and sdcard..

any solution

---

### Post by coffeecat on 2011-08-26
What exactly are you asking? 

ntfs-3g is the driver for NTFS filesystems. If the partition has a NTFS filesystem then the system needs ntfs-3g to read it - you do not want to remove the ntfs-3g driver.

If you are getting I/O errors then provide details and someone may be able to help.

---

### Post by zissshh on 2011-08-26
Maybe the ntfs partitons are creating problems,,,any thread that provide detailed process to remove my existing partition into linux ext3

theres already a thread desicated to my I/o error,,
[http://ubuntuforums.org/showthread.php?t=1708735]("http://ubuntuforums.org/showthread.php?t=1708735")

---

### Post by coffeecat on 2011-08-26
I don't have time to read the 30 posts in that thread but as far as I can make out your I/O errors were due to typos you made in the terminal.

I very much doubt that a NTFS filesystem is causing problems. Why don't you use the GUI to copy files and create folders? What happens when you do that?

---

### Post by zissshh on 2011-08-26
Pls be specific about gui,,,,

---

### Post by coffeecat on 2011-08-26
> **zissshh said:**
> Pls be specific about gui,,,,

GUI = Graphical User Interface. Your desktop.

Your other thread showed that you were having trouble with terminal syntax when copying files or creating folders. All I am suggesting is that you use a file browser in the graphical desktop to copy files from/to the partition you believe you are having problems with, and to make new folders. If you can do that then there is nothing wrong with your partitions. But if you get errors in the GUI, then post those.

---

