---
title: "How Can I Install an Additional SATA Drive"
date: 2014-03-20
forum: Hardware
---

### Post by BudTuba on 2014-03-20
I recently replaced my computer MB with an older EP-8KARI-X  motherboard that was lent to me until I could buy a new MB.  The bios  does not recognize SATA drives for booting, so I mounted a 250GB SATA  drive into a USB-SATA box and proceeded to install Ubuntu 12.04 using an  active CD.  The installation went well and I can use Ubuntu and boot  from this USB interface.  I then installed a second 500GB SATA drive  into into the computer.  Using Disk Utility, I had hoped to be able to  mount this drive.  It was partitioned in two 250GB partitions in my old  computer, one being ntfs and the other ext3.  I had hoped to be able to  install Win XP on the ntfs partition, but it does not show up.  I tried  listing devices in /media/ and found only floppy and floppy(o).  


  Can anyone help a beginner figure out how to mount the added SATA drive?

  Is there a command to probe for it, or a program?:lolflag:

---

### Post by Bashing-om on 2014-03-20
BudTuba; Hi !

See if this link helps.
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

[INDENT]I do hope this helps
[/INDENT]

---

### Post by Yellow Pasque on 2014-03-21
Does the BIOS recognize the drive? I'm not sure what chipset an EP-8KARI-X uses, but if it's from the early days of SATA, a lot of the southbridges (nforce 2/3, intel ich 4/5, via 8237) had issues recognizing SATA 300Gbps drives, and the drive would have to be jumpered to force SATA 150Gbps speed.

---

### Post by BudTuba on 2014-03-22
What kind of "jumpered" do you mean?  This is a 500GB drive with two partitions, one as NTFS and one as ext2 or 3.  There is a four pin place adjacent to the SATA cable.  Is this what you mean?

BTW..thanks for the suggestion.

---

### Post by BudTuba on 2014-03-22
Thanks for the suggestion, but:

I read that and it seems to be for only U 10.04.  I have installed U 12.04.  Being a beginner, much of this is Greek to me.  The suggestion to check /dev/mapper/ yielded a program control.  
/dev/disk$ sudo dmraid -ay
no raid disks

So this command doesn't activate the search for SATA disks, only lists, and in this case, found none.

---

### Post by Yellow Pasque on 2014-03-22
Does the BIOS recognize the drive?

---

