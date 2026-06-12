---
title: "Cannot do fresh install Ubuntu 9.10"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by blegs38552 on 2009-11-10
I downloaded the ISO to my Windows 7 laptop and used Win 7's ISO Burn to Disk option to burn to a CD-R. Rebooted and got the language screen. I chose English and got the menu with 4 different options. I clicked the option 2 to do a full install and nothing further happened - I heard the CD drive briefly read the CD, but nothing more, and the menu screen stayed up. I finally chose option 4 to boot to Windows. I downloaded again from a different site and burnt to a CD-RW - same result. The file that I downloaded is "ubuntu-9.10-desktop-i386.iso". 

I have a dual partitioned laptop - my c:\ drive is my Windows and Applications drive. My d:\ drive is all of my data files. I also have a USB External HDD connected. My CD drive is my first boot option, and I am able to boot from the Ubuntu CD, but cannot install the O/S.

I previously had 9.04 installed, but was unhappy with the upgrade experience and decided to delete the Ubuntu partitions, combine them with my c:\ drive and start from scratch. My intent is to create the Ubuntu and swap drives from my c:\ drive, but haven't gotten that far.

---

### Post by presence1960 on 2009-11-10
Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso prior to burning to CD?

Did you burn the iso as an image to CD at no more than 4x-8x speed? If your burner does not allow you to select burn speed then see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for InfraRecorder.

When you boot the Live CD/USB choose "Check disk for defects".

I would look at these things first & if they all check out then post back if you continue to have problems.

---

### Post by dhavalbbhatt on 2009-11-10
> **blegs38552 said:**
> I downloaded the ISO to my Windows 7 laptop and used Win 7's ISO Burn to Disk option to burn to a CD-R. Rebooted and got the language screen. I chose English and got the menu with 4 different options. I clicked the option 2 to do a full install and nothing further happened - I heard the CD drive briefly read the CD, but nothing more, and the menu screen stayed up. I finally chose option 4 to boot to Windows. I downloaded again from a different site and burnt to a CD-RW - same result. The file that I downloaded is "ubuntu-9.10-desktop-i386.iso". 

I have a dual partitioned laptop - my c:\ drive is my Windows and Applications drive. My d:\ drive is all of my data files. I also have a USB External HDD connected. My CD drive is my first boot option, and I am able to boot from the Ubuntu CD, but cannot install the O/S.

I previously had 9.04 installed, but was unhappy with the upgrade experience and decided to delete the Ubuntu partitions, combine them with my c:\ drive and start from scratch. My intent is to create the Ubuntu and swap drives from my c:\ drive, but haven't gotten that far.

The desktop installation CD has issues with partition manager. I would suggest you use the alternate installation CD. Does not have the GUI, but should work.

---

### Post by blegs38552 on 2009-11-14
> **dhavalbbhatt said:**
> The desktop installation CD has issues with partition manager. I would suggest you use the alternate installation CD. Does not have the GUI, but should work.

Used the alternate installation CD and was able to install.

I did test the MD5 hash on both versions - the alternate CD passed, but the desktop 386 ISO did not.

---

