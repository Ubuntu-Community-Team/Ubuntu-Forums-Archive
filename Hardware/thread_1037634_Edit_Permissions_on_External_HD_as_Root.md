---
title: "Edit Permissions on External HD as Root"
date: 2009-01-12
forum: Hardware
---

### Post by Onimuno on 2009-01-12
I want to write files to my external hard drive but I don't have the permissions to. How would I get into the root admin and change the permissions on my hard drive?

---

### Post by Onimuno on 2009-01-12
bump

---

### Post by NumPy on 2009-01-12
Are you trying to edit using the sudo command from command line? Or with Dolphin? If the latter is true an easy way would be to launch dolphin as root from a terminal:
```
sudo dopphin
```
This will open a dolphin session as admin.

---

### Post by Onimuno on 2009-01-12
i dont know what to do....i just want to edit the permisions.

---

### Post by logos34 on 2009-01-12
is it formatted ntfs or ext3?

if the latter:

> I Can Read My USB Storage Device, but I Can't Write to It

If you are having trouble writing to a USB key or external USB hard drive, there are a number of possible causes of the problem.The first and most simple to diagnose is that you may not have permission to write to the device. When you plug in the drive, right-click the icon that appears on your desktop, and select Properties. In the window that appears, click the Permissions tab and ensure that the Others line has the Write checkbox selected. If this is not selected, you don't have permission to access the drive.Quick TipIf you do have sufficient permissions but still can't write to the drive, jump to the Filesystem Fun section below.To change these permissions, fire up a terminal, and move to the /media folder:


foo@bar:~$ cd /media


Now take a look at which drives are in there:


foo@bar:~$ ls -al


In the output that appears you should see "usbdisk" as one of the entries. Now change the permissions so everyone can access it:


foo@bar:~$ sudo chmod a+w usbdisk


You should now be able to access the disk.

---

### Post by velophil on 2009-01-14
hye logos34.

this definitely helped me to access my ext disk. i formatted it to ext3 the other day and wasnt able to write to it, thanks a bunch. however, the disk is very very slow when writing or copying from it with ubuntu.
when plugged into a windows PC its superfast! do you know an answer to that one? :)
cheers

velo

---

### Post by logos34 on 2009-01-14
> **velophil said:**
> the disk is very very slow when writing or copying from it with ubuntu.
when plugged into a windows PC its superfast! do you know an answer to that one? :)


maybe it's operating in usb1.1 mode in linux (instead of 2.0) ??? worth a check

---

### Post by velophil on 2009-01-14
hey L,

when i bought the drive it was formatted in NTFS. a quick search on the forum quickly came up with the recommendation to format it to ext3, which i did. but first things first: i run an IBM t41 with two USB2.0 ports. my usb stick works perfectly (sandisk 4 gig, formatted in fat32), superfast transfer rates. this ext hard drive (320 gig medion drive from aldi australia :) ) is giving me trouble. it works perfectly fine on my flatmates EEE PC with winxp, but i am not going backto winxp just for the hard drive ;)
can you tell me how to check and change the speeds for my usb ports? also, the hard drive doesnt support plug and play (properties say its not removable), so if i wantto use it i have to boot it with the PC, which is silly. many questions, hope u can help me out at leastwith a few. thanks heaps in advance.

velo

---

