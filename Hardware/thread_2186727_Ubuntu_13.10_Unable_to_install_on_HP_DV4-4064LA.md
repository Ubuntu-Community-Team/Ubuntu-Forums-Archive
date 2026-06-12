---
title: "Ubuntu 13.10 Unable to install on HP DV4-4064LA"
date: 2013-11-08
forum: Hardware
---

### Post by andreshs22 on 2013-11-08
Hi

I just purchased an HP DV4-4064LA and I have issues installing Ubuntu 64x from the USB or CD, I checked the media and I was able to install it on my Desktop, but on this laptop, at the point on which you will select the partitioning of the HDD to install the OS or modify/create the partitions the installer got stocked, and never detect anything.

Is this a particular issues with the laptop? should I modify anything on the BIOS for the Ubuntu installer to recognize the HDD?

I tried again and left an external HDD connected and it detects the device but ONLY THAT DEVICE, the internal HDD is not recognized.

any one else with this issue?

---

### Post by oldfred on 2013-11-08
Is this a new Windows 8 with UEFI system? Or an older Windows 7 system with all 4 primary partitions used?
Some Windows 8 systems are Ultrabooks and use Intel SRT that has RAID and the RAID meta-data has to be removed before Ubuntu will install.

Post this from terminal in liveDVD or Flash:
sudo parted -l

---

### Post by andreshs22 on 2013-11-09
Hi

thanks for the info, this is a windows 7 laptop but i dont know about the 4 partitions.

I'll check and let you know

---

### Post by oldfred on 2013-11-09
Almost all Windows 7 systems used the 4 primary partitions. A few released just before Windows 8 used UEFI but not secure boot. And some  top of the model Windows 7 systems were Ultrabooks with the small SSD.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

