---
title: "External drive detected, but not mounted"
date: 2010-12-20
forum: Hardware
---

### Post by adm1968 on 2010-12-20
[SIZE="3"]All of my Ubuntu installs have managed to detect my Freecom external HDD correctly.
Not anymore: Lucid refuses to mount it (3 different computers).
The drive does get detected
lsusb
Bus 002 Device 005: ID 07ab:fccd Freecom Technologies

I'm using the same drive on the same 3 computers, connected using the same cable

Any suggestions?

Cheers ;)[/SIZE]

---

### Post by cristianfere on 2010-12-20
> **adm1968 said:**
> [SIZE="3"]All of my Ubuntu installs have managed to detect my Freecom external HDD correctly.
Not anymore: Lucid refuses to mount it (3 different computers).
The drive does get detected
lsusb
Bus 002 Device 005: ID 07ab:fccd Freecom Technologies

I'm using the same drive on the same 3 computers, connected using the same cable

Any suggestions?

Cheers ;)[/SIZE]

Which the file system in the device? 
It work in Windows or in another distro or Ubuntu version?

Check this device in Disk Utility (System/Administration/Disk Utility) and try mount...

---

### Post by Onesimus on 2010-12-20
I had this same problem on my Dell Optiplex 170 - it just refused to mount the drive.  You may get lots of replies asking whether you are providing external power, etc.

I found that rebooting the machine, with it plugged in as it rebooted, managed to then mount the device.  I have no idea why it refused to mount the drive - I just needed to backup my data.

Hope this helps.

---

### Post by adm1968 on 2010-12-20
> **cristianfere said:**
> Which the file system in the device? 
It work in Windows or in another distro or Ubuntu version?

Check this device in Disk Utility (System/Administration/Disk Utility) and try mount...

Thanks!
As I said, the drive has been working perfectly under quite a few earlier versions of Ubuntu (8.04, 8.10, 9.04, and 9.10).
It simply doesn't work any longer under Ubuntu 10.04.

---

### Post by adm1968 on 2010-12-20
> **Onesimus said:**
> I had this same problem on my Dell Optiplex 170 - it just refused to mount the drive.  You may get lots of replies asking whether you are providing external power, etc.

I found that rebooting the machine, with it plugged in as it rebooted, managed to then mount the device.  I have no idea why it refused to mount the drive - I just needed to backup my data.

Hope this helps.

I've just resumed from hibernation, no luck.
Will try with a proper restart.

---

### Post by adm1968 on 2010-12-22
> **Onesimus said:**
> I had this same problem on my Dell Optiplex 170 - it just refused to mount the drive.  You may get lots of replies asking whether you are providing external power, etc.

I found that rebooting the machine, with it plugged in as it rebooted, managed to then mount the device.  I have no idea why it refused to mount the drive - I just needed to backup my data.

Hope this helps.

No luck after a fresh restart, Onesimus
I am just wondering why Ubuntu 10.04 has stopped mounting a drive which has been used before with 8.10, 9.04, and 9.10 :confused::confused:

---

### Post by adm1968 on 2010-12-30
[FONT="Georgia"][SIZE="2"]Anybody else?[/SIZE][/FONT]

---

### Post by Idefix82 on 2010-12-30
You still haven't answered cristianfere's question: what is the file system on the hard drive?

---

