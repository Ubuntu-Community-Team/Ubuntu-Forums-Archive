---
title: "Need help getting Ubuntu to recognize external hd (NTFS) used previously in Windows"
date: 2008-11-15
forum: Hardware
---

### Post by marcusau2 on 2008-11-15
I have recently installed Ubuntu 8.10 on my laptop without a Windows partition.  I have an external hard drive that I backed up all of my files from my previous Windows install.  When I connect my external hd to the computer using usb the activity light turns from green to orange and stays that way.  Ubuntu doesn't recognize the device at all.  The Ubuntu is using an ext3 file system and the external hd is NTFS.  Is there a way through a program, drivers, etc to allow Ubuntu to recognize and mount this drive.  I can't reformat this drive as its contents are too valuable to lose and I don't have any other drives available to store them on temporarily.  I have browsed many forums and one suggested the NTFS configuration tool.  I installed this and enabled support for NTFS and I'm still getting no response.  I would appreciate any help/assistance available.  Thanks.

---

### Post by Rayaz on 2008-11-15
Have you used the external drive with ubuntu before? If not, are you running the hard drive with jumper set to master?

---

### Post by cdtech on 2008-11-15
With the USB drive connected, what is the output (in a terminal) of:
```
sudo fdisk -l
```

---

### Post by marcusau2 on 2008-11-15
I used the drive on Ubuntu using the Wubi dual boot install when I was considering whether to make the full transition to linux.  The file system during that install was NTFS if I'm not mistaken.  The install didn't create a separate partition and the drive worked fine with Windows. I'm not sure whether it was set to slave or master.  Wouldn't it have to be slave in order to be recognized as a plug and play device?  BTW I am not at home with my external drive. I thought I'd post this while I'm away to get some responses before I return.

---

### Post by cdtech on 2008-11-15
The USB cable has no signal switching capabilities to the Motherboard and only has one signal path, so use the master jumper setting.

---

