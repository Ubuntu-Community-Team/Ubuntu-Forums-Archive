---
title: "Promise TX2300 Ubuntu 8.04 and RAID1"
date: 2008-11-15
forum: Hardware
---

### Post by AlexD1979 on 2008-11-15
Hello,
I have a Utuntu 8.04 64Bit installed with DELL PC on-Board Controller and only one Samsung 250 GB HDD. After that I add the TX2300, plug the HDD1 to Port 1 and HDD2 to Port 2 and build a RAID 1. That works fine, the Server going on works!
But, now if I try to test some cases of failure, the Raid controller fails. e.g. I unplug the power cord from HDD 1 when the server is up and works. I see some messages on the linux console (Some lines sd 0:0:0:0 rejecting I/O to offline device, Buffer I/O error on device sda1,logical block 123123123, EXT3-fs error (device sda1): ext3_find_entry: reading directory 2777712 offset 0 and so on) and after that, I cannot make any command till I reboot. After I reboot the server hard reset, everything is ok with one remaining HDD. Does this Controller not support a hot-failure if one drive became defect?
Is there a very good HowTo to get the Server wotk with "full RAID 1" functionally?

---

### Post by cariboo on 2008-11-15
Are you using dmraid to control your raid array? If you are, in a terminal type:

```
man dmraid
```

For more info.

Jim

---

### Post by AlexD1979 on 2008-11-17
> **cariboo907 said:**
> Are you using dmraid to control your raid array? If you are, in a terminal type:

```
man dmraid
```

For more info.

Jim

Why? I think it is a Hardware Raidcontroller and so i think the Raid functionality is working transparent in the background without of attaching the installed OS.

---

### Post by AlexD1979 on 2008-11-17
Has nobody any experinces with TX2300 and Linux?

---

