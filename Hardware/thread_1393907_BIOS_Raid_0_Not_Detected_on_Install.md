---
title: "BIOS Raid 0 Not Detected on Install"
date: 2010-01-29
forum: Hardware
---

### Post by marbaugh on 2010-01-29
I am have a GA-MA78GM-US2H motherboard with two 500GIG hard drives that are RAID 0 together using the promise fasttrack controller.  During the install for Ubuntu 9.10 the RAID 0 is not found and the two 500GIG drives are shown separately.

I have read MANY forums but have had no success getting the installer to detected the RAID 0

---

### Post by tgalati4 on 2010-01-30
How, exactly did you set up the RAID drives?  Did you use the BIOS or a Promise installer disk?

Do you really need RAID0?  What do you expect the benefits to be?

---

### Post by marbaugh on 2010-01-30
I used the BIOS setup to create the RAID.  

I was thinking of creating a software RAID, but I wanted to be able to dual boot the machines with Windows and Linux so I needed the BIOS to take care of the RAID.

Also, I do not really need the RAID 0, I was just very interested in setting it up on the home machine since I have 2 of the same 500GB drives.  I also have an external drives for backups, so I figured RAID 0 would be the best bet so I don't loose any space.

---

### Post by tgalati4 on 2010-01-30
If you installed Windows first, then Windows would write the RAID headers to both drives.  I'm not sure you can dual-boot with RAID.  The one install that I tried failed with Windows XP Media 64-bit and Linux Mint dual boot.  I gave up on it and did a simple dual-boot install on a single drive.  I used the second drive for data.

It's possible that the ubiquity installer doesn't know how to handle Windows-formatted RAID array.  Someone else will have to chime in on this.

If you wipe the drives, set up RAID0 in BIOS and install Ubuntu then you should be OK.  Of course installing Windows after that will mess things up.  It's always better to install Windows first because it overwrites the MBR regardless of what you have installed.

---

### Post by marbaugh on 2010-01-30
Yes, I agree the windows install could mess everything up.

The problem is, if I wipe the drives clean, set up a RAID 0 in the BIOS and Install Ubunutu, the RAID is not recognized by the installer....

---

### Post by tgalati4 on 2010-01-30
My only experience is with LSI Megaraid, Intel RAID, and Promise (but Windows only).  So you have at least narrowed down that the Ubiquity installer does not recognized a Promise Fastrack RAID configuration.  Perhaps you can file a bug on the Ubiquity launchpad page.  The developers can give you some tools to try to help debug your situation.

---

