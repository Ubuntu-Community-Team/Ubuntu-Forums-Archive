---
title: "Install freezes / LSI Megaraid SATA 150-4"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by GeekyG on 2009-03-09
Hi All

I tried to install the latest Ubuntu (8.10) on my Dell. It has a LSI MegaRAID SATA 150-4 controller which is many years old now. It is configured with two disks in RAID 1.
 
As the install started, I did not see any problems and it correctly detected the right disk size. However, the screen went to "Formatting 5%" and stopped.
 
My first thought was a driver issue but the disk size was correct and LSI has not had any releases since 2007. RHEL installed without any problems. I verified the DVD.

I found this but don't see how it helps **(how do I load a module at installation?)**


NAME

      amr - MegaRAID SCSI/ATA/SATA RAID driver
 

SYNOPSIS

      To compile this driver into the kernel, place the following lines in your
      kernel configuration file:
 
            device pci
            device scbus
            device amr
 
      Alternatively, to load the driver as a module at boot time, place the
      following line in loader.conf(5):
 
            amr_load="YES"

---

### Post by Neo_The_User on 2009-03-09
See whats going on in the ttys. Control Alt F1 - 6. One of them is the verbose.

---

### Post by CaptNibor on 2009-04-20
Although I don't have exactly the same issue, I found the same information while looking for a driver for my HP NetRAID controller card.  It appears to me that the info is for Ubuntu 8.04 LTS and therefore does not apply to 8.10.  I cannot find loader.conf anywhere in 8.10.  What file do I need to add

amr_load="YES"

in order for the amr driver to be loaded on boot?  Or, is there another driver I should be using instead?


Thanks,

Robin

---

