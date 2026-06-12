---
title: "Can't write to CD, USB key or disk"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2009-02-01
Hi,
For some reason best know to the gods of Linux, I have seem to have lost the ability write to CD's,DVD's or USB disks (both key and mobile hard disk).
I can read OK from those devices, I just can't write to them.
This seems to have happened with my update to Ubuntu 8.04.2, kernel 2.6.24-23-generic.
Any idea what I have to reset?

---

### Post by blueboy1 on 2009-02-01
i can't help you. but i have a more basic problem. can you help me install my dongle for my phone on my computer?

---

### Post by Stolea on 2009-02-01
By Dongle, I assume you mean a bluetooth decice?
Make sure bluetooth is activated in System-Administration-Services.
If that is done, your device should be recognised.
If its a USB cable, it may or may not recognise the phone. Most phone software only works in Windoze.
You could also go to the manufacturer's site and look up drivers for your device.
Good Luck

---

### Post by bettlebrox on 2009-02-01
> **Stolea said:**
> Hi,
For some reason best know to the gods of Linux, I have seem to have lost the ability write to CD's,DVD's or USB disks (both key and mobile hard disk).
This seems to have happened with my update to Ubuntu 8.04.2, kernel 2.6.24-23-generic.
Any idea what I have to reset?
Verify that you are still in the plugdev & cdrom groups (use the id command).

---

### Post by Stolea on 2009-02-01
Please explain how.

---

### Post by Stolea on 2009-02-02
Anyone with any suggestions? Please.

---

### Post by bettlebrox on 2009-02-02
> **Stolea said:**
> Please explain how.
No problem! :)

Click on System->Administration->Users and Groups
Click on unlock, then click on your user ID, then click Properties, then User Privileges.

Then see if the check boxs for the following are checked:
Access external storage devices
User CD-ROM 
...
Then logout and log back in.

If they are already checked, open a terminal and paste the output of this command:
[INDENT]groups[/INDENT]

---

### Post by Stolea on 2009-02-02
> **bettlebrox said:**
> No problem! :)

Click on System->Administration->Users and Groups
Click on unlock, then click on your user ID, then click Properties, then User Privileges.

Then see if the check boxs for the following are checked:
Access external storage devices
User CD-ROM 
...
Then logout and log back in.

If they are already checked, open a terminal and paste the output of this command:
[INDENT]groups[/INDENT]

This is my output:
> peter@Shop:~$ sudo groups
sudo: unable to resolve host Shop
[sudo] password for peter: 
root
peter@Shop:~$ 


All the appropriate boxes were ticked.

---

### Post by bettlebrox on 2009-02-03
Just run the groups command without sudo.

---

### Post by Stolea on 2009-02-04
peter adm dialout fax cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare

It would appear that I didn't have any room to create temp files need in the process.
I discovered that I had a heap of trash files cluttering up my disk. It took some time to track it down and the to delete it. It would appear that sudo nautilus creates trash files that are hidden. Shift-Delete bypasses that trash bin.

The reason I could not write to the usb stick might have had something to do it having been used to tranfer music from a Mac to my computer. I reformated the stick with Windoze and everything works now.

Life is good once again in Stolea land. :)
Cheers and thanks for your help.

---

