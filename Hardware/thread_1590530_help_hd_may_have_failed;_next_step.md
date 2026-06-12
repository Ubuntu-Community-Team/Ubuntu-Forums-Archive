---
title: "help: hd may have failed; next step"
date: 2010-10-08
forum: Hardware
---

### Post by miesnerd on 2010-10-08
I have a 1 TB HD with a lot of really important personal data on it and its pretty new <1 year old.

It seems like the hard drive just all the sudden stopped being able to mount.

I dont know what the next steps are to determine if the drive died, or what.

Here is the output I think is necessary:
```
sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000481ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System

```

and in case its helpful:```
 lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)
Bus 003 Device 004: ID 046d:c71c Logitech, Inc. 
Bus 003 Device 003: ID 046d:c71b Logitech, Inc. 
Bus 003 Device 002: ID 046d:0b06 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:006a Microsoft Corp. Wireless Optical Mouse (IntelliPoint)
Bus 002 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 010: ID 1058:1100 Western Digital Technologies, Inc. **
Bus 001 Device 005: ID 0d8c:5200 C-Media Electronics, Inc. Mass Storage Controller(0D8C,5200)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Dark_Stang on 2010-10-08
If it really failed, then the more you mess with it the harder data recovery will be. I know a lot of people will suggest doing things yourself. But an amature screwing around can take the cost of a professional data recovery service from $250 to $1500. So if you really do have important data on it, I would recommend taking it to somebody who can do data recovery for you. If you're in the states Best Buy and Office Depot both offer data recovery services. Best Buy's stuff will go to their Louisville service center which houses their data recovery lab. I'm not familiar with Office Depot, but they used to just pass it off to another company.

---

### Post by miesnerd on 2010-10-08
> **Dark_Stang said:**
> If it really failed, then the more you mess with it the harder data recovery will be. I know a lot of people will suggest doing things yourself. But an amature screwing around can take the cost of a professional data recovery service from $250 to $1500. So if you really do have important data on it, I would recommend taking it to somebody who can do data recovery for you. If you're in the states Best Buy and Office Depot both offer data recovery services. Best Buy's stuff will go to their Louisville service center which houses their data recovery lab. I'm not familiar with Office Depot, but they used to just pass it off to another company.

Can/will they recover from an ext3 drive?
I've heard a lot of crap about best buy not being confidential or discrete about information. I mean, I dont have anything to hide, but still, I'd like to first see if I can figure out what the deal is (without messing with it too much, of course).

Really, I'm hoping theres some way to force it to mount, or something?

---

### Post by miesnerd on 2010-10-09
wanted to update this; testdisk fixed the problem perfectly.
Drive is easily accessible, no data lost. 
Running diagnostics now to ensure all is truly well.

Miesnerd

---

### Post by Dark_Stang on 2010-10-09
Make sure you don't have bad sectors, they tend to spread like cancer. If you find bad sectors, don't bother "repairing" them. All that does is try to move the data off the sector and flag it not to be used anymore. This is like giving a stabbing victum a bandaid.

As for the Best Buy stuff, I was a Geek Squad agent for 3 years (not anymore, developing now). Their data recovery lab actually runs a highly customized Gentoo build on all it's data recovery machines. So doing data recovery on ext3 is no problem. The more difficult stuff is doing RAID recoveries where the controller has also failed, those also get pretty expensive. Also, Best Buy/Geek Squad has the strictest data privacy rules I have ever seen. With thousands of stores world wide, a mistake is bound to happen some time. But nobody would ever snoop around in your stuff. Plus, the average data privacy dispute costs Best Buy over $50,000. That is a pretty big incentive not to screw up.

---

### Post by miesnerd on 2010-10-09
Thanks for the advice dark stang.

Per the data confidentiality, as an undergrad in college I got software from a best buy geek friend of mine. Where did he get it? A university professor brought it in, he told me this. He even identified who the professor was. So it does happen.

Plus, I'm a nerd. Why not give it a try, right? ;)

---

### Post by Dark_Stang on 2010-10-09
> **miesnerd said:**
> Thanks for the advice dark stang.

Per the data confidentiality, as an undergrad in college I got software from a best buy geek friend of mine. Where did he get it? A university professor brought it in, he told me this. He even identified who the professor was. So it does happen.

Plus, I'm a nerd. Why not give it a try, right? ;)
If I ever met that friend of yours I would turn his reproductive organs into a sadistic piece of art. He isn't professional enough to work in any IT field. With any luck he'll spend most of his life being violated in prison for his deeds.

---

