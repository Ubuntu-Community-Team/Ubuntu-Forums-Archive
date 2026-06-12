---
title: "weird 9.10 issues"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by codfan9 on 2009-11-06
hello ubuntu forums

im new here but have been using 9.04 for a while now after converting from windows. all was well until i decided to upgrade to 9.10. i am wondering how i go about getting rid of 9.04 to do a clean install? im doing this as opposed to upgrading through the manager as ive upgraded, booted, failed to boot and am now locked out of everything including terminal (due to not responding well to my fully operational keyboard meaning i cannot input my password to do anything :S)

also, can anyone recommend a good download as it seems many people are having grub issues.

thank you all in advance):P

ps can anyone tell me where to find the program that builds your distro onto a usb flash drive please?

---

### Post by raymondh on 2009-11-06
> **codfan9 said:**
> hello ubuntu forums

im new here but have been using 9.04 for a while now after converting from windows. all was well until i decided to upgrade to 9.10. i am wondering how i go about getting rid of 9.04 to do a clean install? im doing this as opposed to upgrading through the manager as ive upgraded, booted, failed to boot and am now locked out of everything including terminal (due to not responding well to my fully operational keyboard meaning i cannot input my password to do anything :S)

also, can anyone recommend a good download as it seems many people are having grub issues.

thank you all in advance):P

Use the torrent to download.

Do you want to get rid of 9.10 and re-install Jaunty (9.04)?  If yes, just install jaunty over the existing 9.10.  You can choose MANUAL in step 4 of the install process for this.

-  Back-up your files
-  Boot into the liveCD of jaunty and proceed to install
-  In step 4, select manual
-  Click to highlight the existing ubuntu install (it'll have an ext file format)
-  select EDIT  > USE AS > select mountpoint root (/) > Format to ext3 or ext4
* If you have a separate /home, do the same process.  If you want to retain your current settings, files configs, DO NOT FORMAT.  If you want to start anew, then FORMAT to ext3 or ext4.
-  Review and apply
-  At this point, no need to touch swap unless you want to change its' size or location.

If you want more guidance, post back a screenshot of gparted so the forum can visualize how you have 9.10 karmic currently set up.

Regards,

---

### Post by raymondh on 2009-11-06
> **codfan9 said:**
> 

ps can anyone tell me where to find the program that builds your distro onto a usb flash drive please?

Unetbootin .... or Ubuntu has the USB creator.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by dhavalbbhatt on 2009-11-06
> **codfan9 said:**
> hello ubuntu forums

im new here but have been using 9.04 for a while now after converting from windows. all was well until i decided to upgrade to 9.10. i am wondering how i go about getting rid of 9.04 to do a clean install? im doing this as opposed to upgrading through the manager as ive upgraded, booted, failed to boot and am now locked out of everything including terminal (due to not responding well to my fully operational keyboard meaning i cannot input my password to do anything :S)

also, can anyone recommend a good download as it seems many people are having grub issues.

thank you all in advance):P

ps can anyone tell me where to find the program that builds your distro onto a usb flash drive please?

If you only want to install Ubuntu on your machine, just pop in either the desktop installation CD or the alternate installation CD (for 9.10, I recommend you use alternate CD and not desktop installation CD, since there are issues with Partition Manager on the desktop installation CD) and select "Use entire disk" option at the time of partitioning. That will re-format your disk and install Ubuntu on your computer.

With regards to where to download Ubuntu from - download it as a torrent.

---

