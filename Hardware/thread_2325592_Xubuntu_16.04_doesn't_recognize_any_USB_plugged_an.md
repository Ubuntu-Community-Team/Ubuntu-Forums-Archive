---
title: "Xubuntu 16.04 doesn't recognize any USB plugged android device"
date: 2016-05-23
forum: Hardware
---

### Post by Jordi_Alfonso_Cam on 2016-05-23
Hi to all!

I was running a 14.04 LTS version of xubuntu when my laptop starts to doesn't recognize my android devices when I plug them via USB.
I thought that upgrade to 16.04 will solve the problem, but I was wrong.

When I plug the device the laptop can see it:

```
drjalfonso@Miko-Aspire-5715Z:~$ lsusb
Bus 002 Device 074: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 002 Device 073: ID 192f:0916 Avago Technologies, Pte. 
Bus 002 Device 072: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 002: ID 5986:0102 Acer, Inc Crystal Eye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

but no filesystem was mouted, no file explorer was opened... nothing. xubuntu has no reaction to this pluggued device.
But it works fine when I plug a USB drive... no problems.

i try to get help from forums but i have no luck.

Anybody, please?

PD) forget my language mistakes, english is not my mail lingua.

---

### Post by thenh813 on 2016-05-24
I don't think anything happens automatically when an Android device is plugged in. At least not by default.
Are mtp-tools, mtpfs and gmtp installed? Do you have a data transfer client for MTP (like gmtp) installed?

Please see this guide for more info on how to transfer files between Ubuntu and a Android device.
[http://news.softpedia.com/news/How-to-Transfer-Files-from-Ubuntu-to-Android-341722.shtml](http://news.softpedia.com/news/How-to-Transfer-Files-from-Ubuntu-to-Android-341722.shtml)

---

### Post by Jordi_Alfonso_Cam on 2016-05-24
Well... some weeks ago (about 1 or 2 month) when I plug either my Samsung Galaxy Tab4 or my BQ Aquaris 4.5, automatically Xubuntu detects it, mount it and opens a file explorer window. Exactly the same that happens when I plug a USB pendrive.

I had installed mtp-tools, mtpfs, but not gmtp. I have installed the last one and executed it. This is the report:

```
drjalfonso@Miko-Aspire-5715Z:~$ gmtp
Device 0 (VID=2a47 and PID=2008) is a bq Krillin (MTP).
Android device detected, assigning default bug flags

```

...and freeze. I need to Control+C to get out.

It's not working and i don't know why...

---

