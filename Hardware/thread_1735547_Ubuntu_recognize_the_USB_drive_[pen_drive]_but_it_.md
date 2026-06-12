---
title: "Ubuntu recognize the USB drive [pen drive] but it doesn't show it on MY COMPUTER"
date: 2011-04-21
forum: Hardware
---

### Post by henriquecofa on 2011-04-21
Hello guys, how are you? I hope fine..
well my problem is:
I have just installed Ubuntu 10.10, and I'm trying to upload the files to my notebook, but the USB drive I'm using[a kingston pendrive and an external HD] are not appearing on MY COMPUTER.
I know the system recognize the devices because I checked it using this:

:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 15d9:0a4d Trust International B.V.
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 011: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive / Patriot Xporter 32GB (PEF32GUSB) Flash Drive**
Bus 002 Device 003: ID 04f2:b178 Chicony Electronics Co., Ltd
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And I checked on System>>Administration>>Disk Utilization as well, and it is there...

But the point is: how do I access it? I mean, how do I open it to retrieve the files that are there?

---

### Post by DaveS4 on 2011-04-22
> **henriquecofa said:**
> Hello guys, how are you? I hope fine..
well my problem is:
I have just installed Ubuntu 10.10, and I'm trying to upload the files to my notebook, but the USB drive I'm using[a kingston pendrive and an external HD] are not appearing on MY COMPUTER.
I know the system recognize the devices because I checked it using this:

:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 15d9:0a4d Trust International B.V.
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 011: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive / Patriot Xporter 32GB (PEF32GUSB) Flash Drive**
Bus 002 Device 003: ID 04f2:b178 Chicony Electronics Co., Ltd
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And I checked on System>>Administration>>Disk Utilization as well, and it is there...

But the point is: how do I access it? I mean, how do I open it to retrieve the files that are there?


I wish I had an answer for you. It looks like I'm having the same problem. Ubuntu recognized usb devices, but I'm unable to have any communication between the computer and the usb device.... iPod, printer, phone, flash drive... none of it works. 

And I've had no luck in this forum either. But I'm thinking that this is a legit bug, and somebody needs to let us know if there's a fix. 

Good luck to you.

---

### Post by henriquecofa on 2011-04-22
Hello Dave, how is it going?
Well, I've asked help in many different forums beside this one. Actually everything they asked me to do, I did, but nothing worked. This is the first time I give up Windows for good, and it has been really great[beside this little issue].

And you know what? I noticed that my External HD worked just when my pendrive was plugged in first, isn't that wierd?:confused:

Well, at least it worked this way, otherwise i'd be screwed for sure. My pendrive is dead so far... no communication.

I hope they fix it with Ubuntu 11.04!

---

### Post by cavalier911 on 2011-04-22
menu/Accessories/File Manager
Drive icons appear on left column.
Clicking on the drive icon in the left column will make contents of drive appear in right window.
File manager Edit/Preferences/Volume Management controls how your notified and if drives are auto mounted when plugged in.
The system works in Lubuntu Lucid 10.04 LTS

---

### Post by jchw on 2011-05-14
I have exactly the same problem and I have tried the forum without success. Although I can now see the stick drive after deleting usbmount I cannot move data into or out of the drive.

I use a 32G usb stick as a backup device and for me this is quite serious. There appears to be no immediate solution so as a precaution I am moving all my data into Mint. Hopefully the last backup done in Deja Dup will work in Mint and effectively transfer the data. It looks like I will lose about a weeks worth of data.

My 4 sticks all worked very well until about a week ago and they work OK in Mint so it is a Ubuntu issue.

I question whether this is a problem stemming from a routine update (not the 11.4 upgrade) and if so should it be reported as a bug?

---

