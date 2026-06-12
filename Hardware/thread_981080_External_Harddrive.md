---
title: "External Harddrive"
date: 2008-11-13
forum: Hardware
---

### Post by TheManzine on 2008-11-13
Hi everyone, I am having a problem with an external hard drive I use for my school work in IT and I definitely have an issue and I can't afford to lose all of my information. My hard drive is a 250gb Comstar external and the plug n play worked fine with vista and ubuntu both but ubuntu needs you to properly click the "Safely remove hardware" before you disconnect it in windows or else ubuntu won't be able to mount it. So that's not a problem and it was working fine but when I was in the process of mving my harddrive from one operating system to another in between my laptop and desktop the harddrive stopped working entirely. When I plug it in now it just makes a strange noise it never made before and I am praying to god I haven't lost everything. Does anyone know what to do, I googled some situations like this but I check device manager and I didn't see it still recognized in windows. Should I try and download the drivers for the external or? This has happened before but it always was fixed with a restart and windows would see it again but the only thing that has freaked me out is that weird noise its making now. Any help would be greatly appreciated.

---

### Post by taurus on 2008-11-13
What is the output when you run this command from a terminal?

```
sudo fdisk -l
```

---

### Post by TheManzine on 2008-11-13
I tried that in terminal and it said fdisk -1 was an invalid option.

---

### Post by dje on 2008-11-13
> **TheManzine said:**
> I tried that in terminal and it said fdisk -1 was an invalid option.

it is a lower case L (l) not a 1 ;)

---

### Post by TheManzine on 2008-11-13
Oops thanks for telling me I can barely notice the difference with the font I have on right now. This was my output from the sudo fdisk -l cmd```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ff86206

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1227     9850880   27  Unknown
/dev/sda2   *        1227       21772   165028052    7  HPFS/NTFS
/dev/sda3           21773       24209    19575202+  83  Linux
/dev/sda4           24210       24321      899640    5  Extended
/dev/sda5           24210       24321      899608+  82  Linux swap / Solaris

```

---

### Post by TheManzine on 2008-11-13
My hard drive is still plugged in but the weird noise has stopped. I don't know if that is good or bad at this point ugh. From my output I don't see that it's showing my drive as the first two sda's are for my windows partitions.

---

### Post by taurus on 2008-11-13
How about 

```
dmesg | tail
```

---

### Post by TheManzine on 2008-11-13
```
[   65.956894]  domain 0: span 03
[   65.956897]   groups: 02 01
[   69.407135] NET: Registered protocol family 17
[   72.710093] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.647221] wlan0: no IPv6 routers present
[  366.033895] hub 2-0:1.0: over-current change on port 1
[  366.047967] hub 2-0:1.0: over-current change on port 2
[  366.058976] hub 2-0:1.0: over-current change on port 1
[  366.064853] hub 5-0:1.0: over-current change on port 1
[  366.074068] hub 5-0:1.0: over-current change on port 2

```This is what it printed out.

---

### Post by taurus on 2008-11-13
And you did plug in that external harddrive with power on, right?  Try unplugging it and plug it back in and post the output of that command again.  

Otherwise, boot into vista and see if you can read that external drive from windows.

---

### Post by TheManzine on 2008-11-13
My hard drive is one without an external power source and I unplugged it and plugged it back in and typed the same command and here was my output. ```
[   65.956894]  domain 0: span 03
[   65.956897]   groups: 02 01
[   69.407135] NET: Registered protocol family 17
[   72.710093] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   88.647221] wlan0: no IPv6 routers present
[  366.033895] hub 2-0:1.0: over-current change on port 1
[  366.047967] hub 2-0:1.0: over-current change on port 2
[  366.058976] hub 2-0:1.0: over-current change on port 1
[  366.064853] hub 5-0:1.0: over-current change on port 1
[  366.074068] hub 5-0:1.0: over-current change on port 2

```I'm pretty sure its the same and I'll try to go back into windows and check but the last few times I tried to in windows it didn't.

---

### Post by prshah on 2008-11-13
> **TheManzine said:**
> My hard drive is one without an external power 

If it's an external notebook drive (2.5") then you will be supplied with a "Y" cable; ie, two usb plugs to be plugged into the computer, and a single one on the other end to be plugged into the unit.

Plug both usb plugs into the computer first, then plug the other end into the unit. It should be OK.

You cannot have an external drive without either a "Y" cable or an external power source. The "overcurrent" messages you are seeing means that more power is being drawn through USB than the computer can supply.

---

### Post by TheManzine on 2008-11-13
I do have a Y-cord and I usually plug it into the hard drive first and then into the computer but would it be better to do the opposite to plug it into the computer first and then the hard drive? I looked at my device manager in vista and I see the usual "USB mass storage device" and it has a yellow exclamation point above it as if it had an error and it said to fix it to just unplug it and plug it back in. I unplug it and refresh the device manager but it still shows there. Is there some special process to get my device manager in vista to stop holding it there even after I unplug it? I right-clicked on it and updated the driver but it was already current and there are the options to uninstall but I don't think I want that and the there is disable but I'm not sure what will fix it. This USB Mass storage device is under my universal serial bus controller listing in device manager.

---

