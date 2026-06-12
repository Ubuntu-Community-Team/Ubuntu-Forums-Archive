---
title: "RAID 0, Dualboot Windows and Ubuntu"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by Flapse on 2009-07-24
Hi!

So I'm kinda new to this Ubuntu thing but i've searched around a little bit, couldn't really find an answer to my issue .

I've got this raid configuration working with my windows 7. The setup is raid 0 and I think the controller is intel(R) Matrix Storage manager ROM v7.5.0.1017.
So I'm trying to install Fakeraid to dualboot with Windows 7. Following this guide [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) , my error occurs at step number six: [FONT=verdana, arial, helvetica][SIZE=2]FATAL ERROR: Bad primary Partition 2: Partition ends in the final partial cylinder" "Press any key to exit cfdisk"...[/SIZE][/FONT] If I (even if i didn't finnish the guide) then try to close down the terminal, I can find the RAID in install, but I can't make a successfull installation. 

So I'm a little bit lost here, please help me out!:confused:

Thanks in advance!

---

### Post by dstew on 2009-07-24
My guess is that cfdisk needs the partition to end on a cylinder boundary. You might have to re-create the partition to make sure that happens.

---

### Post by Flapse on 2009-07-24
Okay, so I'm formating the entire drive, what file system should I use for maximized compability?

---

### Post by dstew on 2009-07-27
Windows uses its own file system (NTFS) and Linux needs ext3 or ext4. You need to create the RAID as though you were installing Windows, but leave room for Ubuntu partitions. Create NTFS partitions from the RAID for Windows, and ext3 or ext4 partitions for Ubuntu. Install Windows first, then try the FakeRAID procedure with dmraid again.

There is really no guarantee that you can get Ubuntu installed onto the RAID, as the How-To says. Eventually, Ubuntu will come up with an installer that automatically installs on FakeRAID.

---

### Post by Flapse on 2009-08-05
So how long might I have to wait for that Ubuntu installer for fakeraid?

---

