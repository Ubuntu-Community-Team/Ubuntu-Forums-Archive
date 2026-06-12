---
title: "HDD Access Issues"
date: 2015-11-05
forum: Hardware
---

### Post by theone964-8 on 2015-11-05
Hello,
So after searching the forum and the web for days I've finally resorted to asking for help.

I have (had) a Lenovo G50-45 Laptop with Windows 8.1. I successfully installed Ubuntu 14.04 on it and everything worked perfectly. I left it on overnight for downloads and when I woke up the next day the screen was blank. I tried to wake it up, without any success.

I've tried every combination I could think of:
[LIST]
[*]Turn laptop on with battery only,
[*]Turn laptop on with AC only,
[*]Turn laptop on with both AC and Battery,
[*]Keep power button pressed for 30  seconds with battery out to discharge,
[*]Reset Memory modules, switched, and tried only one at a time.
[*]Tried another confirmed working HDD
[/LIST]

Nothing works. It won't turn on. The screen remains blank the webcam light comes on when it starts and so does the hdd led. then it stays on for 30 or so seconds and restarts in this endless loop.

Another issue (the main issue i'm really hoping to get help with) is the HDD is not working. I plug it into my desktop and its not being recognised in windows or Ubuntu.
Please give me some advice on this. Thank you in advance.

---

### Post by theone964-8 on 2015-11-06
UPDATE:
OK so after waiting for over an hour with the disk plugged in it finally showed up as sdb after running sudo fdisk -l. it did not show any partitions

I ran testdisk and it showed the HDD. I clicked on proceed and it asked to select the partition type. At the bottom it says Intel was detected but in fdisk-l is siad GPT so which one so I use. also i need help using testdisk, I know its a powerful tool and it has the capability to erase me entire disk. I don't know how to use it so im asking for some help.

---

