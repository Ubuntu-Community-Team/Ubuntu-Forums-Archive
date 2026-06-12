---
title: "motherboard died (urgent)"
date: 2012-11-15
forum: Hardware
---

### Post by elite0083 on 2012-11-15
I had to buy a  new motherboard because my old one crapped out on me, the only problem  is I couldn't get the exact same model and now I get an error when I try  to run ubuntu saying run kernal first. I am currently running from a  live disk, but was wondering if there is anything I can do except  reinstall.

---

### Post by kurt18947 on 2012-11-15
I wonder if you had some proprietary driver installed like  video?  I installed Lubuntu on a hard drive, plugged it into another machine and it ran without issue.  Or the dead MoBo installed something proprietary.  Any PPAs?  They (PPAs) could cause a problem as well.

---

### Post by oldfred on 2012-11-15
When I put in a totally new motherboard, but same generation dual core and new video card but just a newer nvidia card, it just booted without any issue.

Run kernel first seems like it is not finding correct files or locations. Do you have more than one drive, does grub need to be reinstalled. Perhaps a chroot and full update if nothing else.

Lets see where everything is at first. You can download Boot-Repair into your liveCD.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by elite0083 on 2012-11-21
I tried to run bott repair, but to no avail. I had grub coming up and listing everything, but it still wasn't working right. I don't think there was any proprietary stuff because I was using the generic drivers and the on board video card. I tried to redownload 12.04, to see if there was a repair feature, but there wasn't one. I finally gave up and just reinstall it hoping that the new one would recognize the old one and transfer stuff over like it had in the past, but it didn't and I ended up having to start all the way over. thank you guys for the help anyway.

---

