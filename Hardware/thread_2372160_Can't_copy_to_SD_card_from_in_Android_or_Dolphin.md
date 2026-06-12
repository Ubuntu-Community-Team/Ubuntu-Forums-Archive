---
title: "Can't copy to SD card from in Android or Dolphin"
date: 2017-09-22
forum: Hardware
---

### Post by accounts0 on 2017-09-22
When I try to copy to the SD card from Dolphin it shows 0b/s in the transfer window in the KDE system tray, & never progresses. Sometimes I get a red bar at the top that says "Could not make folder /Foo/SD card/Music/Bar".


I can copy from Dolphin to the internal storage, but when I try to move to the SD card in Android, it just fails with a 'Cancelled' error pop-up. I can delete files on the SD card.


Not sure why or when this started.

---

### Post by efflandt on 2017-09-23
I am not familiar with Dolphin (I thought that was Max OSX desktop). When connected to USB I can copy from Ubuntu to either internal storage or external storage (microSD) on my Samsung J7 using nautilus (default file manager). Note that on newer Android versions (I have 6.0.1) /sdcard on the phone is a loop back to internal storage. There is also a block between internal storage and the actual mount location of (micro)SD card if you log into the phone with ssh (or sftp), where from internal storage you have read permission, but NOT write permission to external storage. So for "AndFTP" in Android on the phone (to sftp from that end when connected to LAN), I have 2 separate AndFTP connections set up for internal storage or actual microSD as local system. That was not an issue with earlier Android versions (like 4.3 on my old S3).

With the file manager on the phone itself I can move files between internal storage and microSD, but cannot move files to microSD from any Android terminal program, or any external ssh or sftp. Normally the microSD would be mounted based on its UUID, but since I did not format mine beyond its factory format, it is mounted at /storage/0000-0000 (normally 0000-0000 would be UUID of FAT32 or exFAT). Although, Android 6.0.1 uses ext4 for its internal storage (4.3 used exFAT), it will not accept microSD formatted as ext4 (only FAT32 or exFAT is accepted).

---

### Post by accounts0 on 2017-09-25
> **efflandt said:**
> When connected to USB I can copy from Ubuntu to either internal storage or external storage (microSD) on my Samsung J7 using nautilus (default file manager). 

With the file manager on the phone itself I can move files between internal storage and microSD


It used to be this way several weeks ago.

When I connect it via USB, I have 'File Transfer' mode selected as 'Always'. Which now apparently only provides access to the internal storage.

I'm tempted to reformat it using the internal Android command & see what happens after that, but I'm hesitant since so many apps use it that I dread having to re- set up everything after wiping all that data.

---

### Post by accounts0 on 2017-09-28
So I've reformatted after doing a backup & now I can write but some of my apps are broken after restoring from the backup.

I can paste into & create subfolders in the SD cards' root folders but I can't rename anything unless I do it from the Android's native file manager- not from the computer.

---

### Post by efflandt on 2017-09-29
Do you have a memory card reader that can connect the memory card to the computer? Although that would be a pain to do regularly if you have a case on your phone and have to remove the back of the phone to get to the card.

I had forgotten that my phone with Android 6.0.1 asks me if I want to allow my PC to connect to it when I connect the USB cable to the PC (Android 4.3 worked without asking). 16.10 seemed to pack syslog with so much MTP diagnostic info that I normally just use AndFTP to sftp from my phone when connected to local WiFi. But for that you need to install openssh-server in Ubuntu if you have not already (that also includes openssh-sftp-server).

What Android version do you have?

---

### Post by accounts0 on 2017-09-29
> **efflandt said:**
> Do you have a memory card reader that can connect the memory card to the computer?
No.
> **efflandt said:**
> What Android version do you have?
Nougat IIRC.

---

