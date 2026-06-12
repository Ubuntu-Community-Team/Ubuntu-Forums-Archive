---
title: "au 200 usb skype phone"
date: 2009-08-26
forum: Hardware
---

### Post by makoshark55 on 2009-08-26
I have a au200 USB phone that works great with skype in windows XP. I can get any reaction when I plug in in under ubuntu 9.04. How do I get it recognised? I have a copy of the C++ code for the phone, but I am not much of a programer. I have found for me a project is the best way to learn. It seems to me the first thing I need to do is get ubuntu to see the device first, but I do not know how to test for this? I sure would like to get my skype phone working so I can format windows. the phone is basicaly a keypad with its own sound card.
Thanks in advance

---

### Post by IcarusR on 2009-08-29
Type lsusb in a terminal with the phone plugged in & see if it is listed.
If not you are definitely stuck.
I have googled & can find no info on using this with linux, except on manufacturers site it says they do not & will not support either MAC or Linux.
Suggest you spend you energy on a more doable project.

---

### Post by makoshark55 on 2009-08-29
ok I ran the command once with it pluged in and once without and I brlive it is listed but it has the wrong manufacture listed;  Macronix International Co., Ltd the correct company is Atcom
```

james@james-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 043d:00ff Lexmark International, Inc. InkJet Color Printer
Bus 003 Device 003: ID 043d:007d Lexmark International, Inc. Photo 3150
Bus 003 Device 002: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0851:c080 Macronix International Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:0008 Microsoft Corp. SideWinder Precision Pro
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 8086:0630 Intel Corp. Pocket PC Camera
Bus 005 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
james@james-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 043d:00ff Lexmark International, Inc. InkJet Color Printer
Bus 003 Device 003: ID 043d:007d Lexmark International, Inc. Photo 3150
Bus 003 Device 002: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:0008 Microsoft Corp. SideWinder Precision Pro
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 8086:0630 Intel Corp. Pocket PC Camera
Bus 005 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
james@james-desktop:~$ 

```
So What is my next step to get ubuntu to inter-react with it?

---

### Post by galv on 2011-02-03
> **makoshark55 said:**
> ok I ran the command once with it pluged in and once without and I brlive it is listed but it has the wrong manufacture listed;  Macronix International Co., Ltd the correct company is Atcom
```

james@james-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 043d:00ff Lexmark International, Inc. InkJet Color Printer
Bus 003 Device 003: ID 043d:007d Lexmark International, Inc. Photo 3150
Bus 003 Device 002: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 0851:c080 Macronix International Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:0008 Microsoft Corp. SideWinder Precision Pro
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 8086:0630 Intel Corp. Pocket PC Camera
Bus 005 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
james@james-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 043d:00ff Lexmark International, Inc. InkJet Color Printer
Bus 003 Device 003: ID 043d:007d Lexmark International, Inc. Photo 3150
Bus 003 Device 002: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:0008 Microsoft Corp. SideWinder Precision Pro
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 8086:0630 Intel Corp. Pocket PC Camera
Bus 005 Device 002: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
james@james-desktop:~$ 

```
So What is my next step to get ubuntu to inter-react with it?

Did you get somewhere with this phone?

---

### Post by makoshark55 on 2011-02-03
Nope never got any were. I just ended up buying a used computer for $50 and I run windows on it. I will never do a dual boot again as every time I got the blue screen of death I ended up reinstalling Ubuntu. I won't let windows any were neer my Linux! the spare only runs two programs my skype phone and livezilla live help chat. It seems to run ok with only two programs to run. I can also marvel at how crappy my website looks in IE 8.:lolflag: If anyone needs the code I think I backed it up on my Linux box before the last time windows up chucked. my coding gose as far as hello world and hacking something already coded.):P

---

