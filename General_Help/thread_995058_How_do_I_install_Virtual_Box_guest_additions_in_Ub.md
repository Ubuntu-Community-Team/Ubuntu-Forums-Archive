---
title: "How do I install Virtual Box guest additions in Ubuntu inside Virtual Box"
date: 2008-11-27
forum: General Help
---

### Post by Rytron on 2008-11-27
Hi,
I have Ubuntu as my main OS.
However to test adding new themes I want to install Ubuntu in Windows XP(a dual boot setup) inside Virtual Box.
Ubuntu installed in Virtual Box in XP, I cannot setup virtual box guest additions properly though.
Whats the correct procedure? Also it wont recognise my usb pen drive.
Thanks.

---

### Post by Rytron on 2009-01-27
Anyone? I also need to access my flash drive from inside Virtual Box.

---

### Post by empty_spaces on 2009-01-27
When you start your Ubuntu virtual machine, Click on "Install Guest Additions" from the Devices menu. 

It might look like nothing is happening but the guest additions are being downloaded. They should get mounted automatically on you cd drive and appear on you guest desktop, if not then go to your cd drive in the guest and see if the guest additions are there.

After you see the guest additions files in there, Run sudo sh /media/cdrom/VBoxLinuxAdditions.run, and follow the instructions on screen. You may have to change cdrom to cdrom0 or something depending on what it is called on your guest.

As for your usb questions, please follow the instructions on this link exactly. Please wait for the page to load completely and it will stop at the USB intructions.

[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

These instructions are all I needed to get usb working perfectly. Make sure you follow the Intrepid directions as I see that you are using Intrepid.

Some may say you also need to edit fstab to get usb working, but I think if you follow these intructions exactly, you should not need to edit fstab.

Once you have set up your usb ports, you will need to add filters for each device that you want to use.

---

### Post by sedawk on 2009-01-27
Hello!

Wouldn't it be easier to create a new Ubuntu user to test
new themes, instead of running two Ubuntus?
If you do not need the user anymore delete him and his
home directory completely.

---

### Post by Rytron on 2009-01-27
Good point sedawk.

---

