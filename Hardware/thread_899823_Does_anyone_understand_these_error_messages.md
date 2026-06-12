---
title: "Does anyone understand these error messages?"
date: 2008-08-24
forum: Hardware
---

### Post by zenkaon on 2008-08-24
Hello,

I have a Toshiba Teccra M3 laptop and I was wondering if someone could help me understand some error messages. I think that they may be related to my sata hard disk, which I know has some bad sectors on it. 

Also, I had a fully encrypted installation of ubuntu and recently it refused to unlock the drive even though I am certain that the password was correct. I believe that another bad sector appeared on the hard disk and shafted the whole thing. I have just reinstalled a normal, unencrypted, ubuntu and it froze when doing an upgrade. Now The laptop will let me log in (graphically) but gnome will not load. 

When I boot into safe mode and select "repair broken packages", at the package libsmbios1 the screen fills up with the following, which repeats ad infinitum:

```

ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: BMDMA stat 0x24
ata1.00: cmd c8/00:08:80:36:78/00:00:00:00:00/e5 tag 0 dma 4096 in
ata1.00: status: { DRDY ERR }
ata1.00: error: { UNC }

```
  
Can anybody translate this into english? Offer any advice?

---

### Post by Loaded.len on 2008-08-24
Do you still get those errors after resetting your BIOS to default settings?

Oh, and if you're certain about bad sectors, wouldn't it be a lot less headache and confusion if you replaced the HDD?

---

### Post by zenkaon on 2008-08-24
reset bios to default values. Same error messages.

I am going to send the laptop away as it is still under warranty, but I would like to understand what the errors mean.

Does anyone know how I can do a detailed analysis on the state of my hard disk? I could print this out and send it off to the warranty people.

---

### Post by lswb on 2008-08-24
Those look like the messages you would see in /var/log/syslog when there is a drive error. You will likely see them there or if you run dmesg|more in a terminal. Before you go to the trouble of sending the laptop back, you may want to open up the hard drive cover and make sure that the cable is connected securely (provided it doesn't have one of those "warranty void if removed" stickers over the cover.

---

