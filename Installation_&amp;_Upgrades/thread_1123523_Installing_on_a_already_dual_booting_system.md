---
title: "Installing on a already dual booting system"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by tamarku on 2009-04-12
Hello, I have a question for anyone about installing the latest version of ubuntu over another version of linux that is already installed.  

Here are the details. I have a Toshiba Satellite, 110 GB HDD, 2 Gigs of RAM.  Current set up is that it is dual booting Windows Vista with gOS (which I believe is based on Ubuntu 8.04).  I don't want to add a third OS but I would like to maybe get rid of the gOS and install the latest version of Ubuntu.  Does anyone know or have any suggestions I can follow to do this.  I've tried Ubuntu once before on this same machine but after an update it wouldn't boot anymore.  

Anyway, if anyone has any suggestions or advice I would greatly appreciate it.

Regards, 
Tom

---

### Post by upchucky on 2009-04-12
download gparted, burn the gparted bootable cd, then boot the pc with the cd then use it to delete the gos linux partition, then create a ext3 partition for ubuntu.

remember to only do each partitioning procedure one at a time, so the partitioner does not get locked by confusion.

you may or may not need to manually configure grub to set up the dual boot again this time for ubuntu.

the MBR may still think it has gos, it may need to be redone to see ubuntu.

you will need to edit /boot/grub/menu.lst if it does not boot.

downloading supergrub to fix the MBR should help in this case.

---

### Post by DavidTangye on 2009-04-12
I assume you have gOs and Windoze each in their own partitions. If so you should be able to install Ubuntu into the gOS partition, and at the end of the install, get the grub boot manager to install on the disks MBR. It will see the Windoze setup, and will set itself up to dual boot ubuntu or Windoze.

---

### Post by DavidTangye on 2009-04-12
Why does he need to use gparted. The ubuntu installer has a partition tool and it works fine.

---

### Post by upchucky on 2009-04-12
yup but just having a bootable gparted is knowledge and knowledge is power.

eventually almost everyone needs a standalone partition manager, may as well start off right.

---

### Post by tamarku on 2009-04-12
OK, so if I download the latest version of ubuntu and start the install it should see the Windows partition and the Linux partition.  Then the partition tool that comes with ubuntu should fix grub and do the necessary formatting.  Is that all correct?  Before I do this I also want to make sure ubuntu will work on my laptop.  Which if gOS which is based off of ubuntu 8.04, works then so should ubuntu.  Thanks for the replies!

Regards, 
Tom

---

