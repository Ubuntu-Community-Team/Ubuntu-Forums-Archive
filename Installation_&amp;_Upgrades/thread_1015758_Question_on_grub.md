---
title: "Question on grub"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by texas.chef94 on 2008-12-19
I now have a second PC with 8.10 installed for grandkids and as this 12 year old watched as we installed 8.10 he posed a question when the installation got to grub and installed it.
His question to me and now to you so I can explain it and know myself:
He said his teacher said that most Linux distros ask where to install grub and gives one an option. Plus he had never watched a linux install so when it got to grub he remembered what the teacher said.
I told him I would ask forum.

Thanks

---

### Post by red_team316 on 2008-12-19
That is correct. You can change where GRUB installs the bootloader. 

In the Ubuntu installer, on the last screen before it does the actual install, you should see a button that says Advanced. Click on it and you should see the option of changing the location where the GRUB bootloader is installed. Typically it defaults to (hd0), which installs GRUB to the master boot record on the first hard drive. You can change this line to /dev/sda5 or whatever partition you like. It will then install GRUB to that particular partition rather than the master boot record. This is especially useful if you plan on setting up a multi-boot system.

Please look here for some excellent information on GRUB and the best info on multi-booting I've ever come across.
**How to install and boot 145 operating systems in a PC**
[http://www.justlinux.com/forum/showthread.php?p=861282](http://www.justlinux.com/forum/showthread.php?p=861282)

---

### Post by texas.chef94 on 2008-12-19
> **red_team316 said:**
> That is correct. You can change where GRUB installs the bootloader. 

In the Ubuntu installer, on the last screen before it does the actual install, you should see a button that says Advanced. Click on it and you should see the option of changing the location where the GRUB bootloader is installed. Typically it defaults to (hd0), which installs GRUB to the master boot record on the first hard drive. You can change this line to /dev/sda5 or whatever partition you like. It will then install GRUB to that particular partition rather than the master boot record. This is especially useful if you plan on setting up a multi-boot system.

Please look here for some excellent information on GRUB and the best info on multi-booting I've ever come across.
**How to install and boot 145 operating systems in a PC**
[http://www.justlinux.com/forum/showthread.php?p=861282](http://www.justlinux.com/forum/showthread.php?p=861282)

What an absolutely informative site and 145 OS. I e-mailed that to the grandsons computer class. Thanks

---

### Post by markbuntu on 2008-12-19
I only have 4 os on my computer, all linux. I have one grub at hd(0) and chainload to  other grubs that are on the drives/partitions where the other OSs live. I find that this avoids a lot of problems.

One grub to rule them all!!!

and backup that menu.lst.

---

