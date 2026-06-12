---
title: "External USB Hard Disk Drive help"
date: 2010-08-03
forum: Hardware
---

### Post by nicknefarious on 2010-08-03
I currently have two external hard disk drives I am having major problems with. One is a SeaGate Free Agent and the other a Hitachi which seems actually to be a Western Digital internally.

Both of them have recently stopped working. When I say stopped working I plug them into the USB port and both of them spin and light up but they continue to spin and never mount or connect properly. I can see the Hitachi is making some connection when I look in syslog but I don't know what to make of it.

I have attached segments of the syslog where the Hitachi was plugged in and then removed. However nothing to report from the syslog when the SeaGate was plugged in or removed.

The Hitachi was plugged in at about 11:03:15secs and unplugged at 11:06:15secs. I plugged it in again at 11:07:05secs and unplugged it again at 11:10.

The SeaGate is under warranty but I am concerned about sending it in with the personal data on it. I have tried using SeaTools suggested by SeaGate but it does not recognise the drive. Are then any other ways I can retrieve the info of this drive or at worst ensure all data has been removed before sending back for a Warranty Return?

The Hitachi is not under Warranty but the supplier has offered to replace it. Again I would like to do everything possible to retrieve the data on it, or at worst ensure everything is deleted.

I have also tried plugging both of the drives into my girlfriend's OLD Sony Vaio but it did not recognise either of them as well.

We did have a problem with an SD card from a camera recently which we thought might have been virus related. The problem disappeared after I reformatted the card. But both drives have been in and out of both laptops along with the problematic SD card.

Sorry.... After leaving the SeaGate connected for around 10 minutes it lit up. Didn't connect or mount properly but somewhere it was recognised. I have included it's syslog output in the attached file underneath the Hitachi info.

File was written in text editor but changed the extension to .doc to get around the maximum size of 19.5kb for .txt files.

I am running Ubuntu Lucid 64-bit on a Dell XPS M1530.

Any help is greatly appreciated.

Many thanks,

Nick

---

### Post by zionLobo on 2010-08-11
> **nicknefarious said:**
> I currently have two external hard disk drives I am having major problems with. One is a SeaGate Free Agent and the other a Hitachi which seems actually to be a Western Digital internally.

Both of them have recently stopped working. When I say stopped working I plug them into the USB port and both of them spin and light up but they continue to spin and never mount or connect properly. I can see the Hitachi is making some connection when I look in syslog but I don't know what to make of it.

I have attached segments of the syslog where the Hitachi was plugged in and then removed. However nothing to report from the syslog when the SeaGate was plugged in or removed.

The Hitachi was plugged in at about 11:03:15secs and unplugged at 11:06:15secs. I plugged it in again at 11:07:05secs and unplugged it again at 11:10.

The SeaGate is under warranty but I am concerned about sending it in with the personal data on it. I have tried using SeaTools suggested by SeaGate but it does not recognise the drive. Are then any other ways I can retrieve the info of this drive or at worst ensure all data has been removed before sending back for a Warranty Return?

The Hitachi is not under Warranty but the supplier has offered to replace it. Again I would like to do everything possible to retrieve the data on it, or at worst ensure everything is deleted.

I have also tried plugging both of the drives into my girlfriend's OLD Sony Vaio but it did not recognise either of them as well.

We did have a problem with an SD card from a camera recently which we thought might have been virus related. The problem disappeared after I reformatted the card. But both drives have been in and out of both laptops along with the problematic SD card.

Sorry.... After leaving the SeaGate connected for around 10 minutes it lit up. Didn't connect or mount properly but somewhere it was recognised. I have included it's syslog output in the attached file underneath the Hitachi info.

File was written in text editor but changed the extension to .doc to get around the maximum size of 19.5kb for .txt files.

I am running Ubuntu Lucid 64-bit on a Dell XPS M1530.

Any help is greatly appreciated.

Many thanks,

Nick
I had a similar problem and i just typed this:
zion@Zion:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:070a Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


my system detected the usb hard drive(Western Digital) and then it mounted automatically.

---

