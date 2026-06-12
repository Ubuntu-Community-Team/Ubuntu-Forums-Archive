---
title: "Wubi troubleshooting"
date: 2008-07-12
forum: General Help
---

### Post by weightgain4000 on 2008-07-12
*****************************************************************
Please disregard post Ive decided not to bother with wubi or ubuntu at this stage, it appears too buggy for my use
*****************************************************************

Hello,

Thank you for taking the time to read my post

Ive been trying to install Ubuntu through wubi and Ive been having some problems

Im currently running windows xp x64 all drives using ntfs and recently defraged

tried installing with an older version 804.0 ended up with this error 0x41228

I followed these instructions

Booting problems: Error 15, file not found

Did you install into a (software) raid (0 or 1) or is your disk encrypted?

Wubi does not support software raid (aka fakeraid) or encrypted disks such as Pointsec or Safeboot, you have to install into a partition outside of the raid array and unencrypted. Pure hardware raids should be ok. Note that some "hardware" raids are in fact software ones.

Do you have multiple hard disks?

If the boot problem happens after the Ubuntu installation (after second reboot) and you have multiple disks, sometimes the disk order at boot is wrong (it is a known bug: [WWW] [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497)). In such cases, edit c:\ubuntu\disks\boot\grub\menu.lst. You have to change all the lines "root (hdX,Y)/ubuntu/disks" to "root ()/ubuntu/disks". Also edit the line that starts with "#groot=(hdX,Y)/ubuntu/disks" to "#groot=()/ubuntu/disks".

however \ubuntu\disks\boot\grub\menu.lst was not to be found and I couldnt be bothered trying to find out why

so I decided on the advice of the wiki to download iso 8.04.1 now I get this error 0x41A38 in grub :confused:

did a quick search for the location of the installation log files to include in the post but cant seem to find them (have looked and googled honest)

any suggestions appreciated

*****************************************************************
Please disregard post Ive decided not to bother with wubi or ubuntu at this stage, it appears too buggy for my use
*****************************************************************

---

