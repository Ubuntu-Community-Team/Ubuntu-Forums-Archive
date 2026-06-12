---
title: "Problem with overheating hard disk with Home partition"
date: 2021-07-16
forum: Hardware
---

### Post by mahdimp20 on 2021-07-16
greetings
I just got an ssd for my laptop and I have a 1TB hard drive next to it
After installing Windows, I installed Ubuntu 20.04 next to Windows by creating the root and efi partitions in ssd and creating the home partition in the amount that I had separated from hdd, but after entering Ubuntu, after a short time, I feel its hard disk temperature It goes up for no reason (this problem does not exist in Windows 10). Has anyone ever had this problem? If you have a solution, thank you for your help.
The format of home and root partitions is ext4 and I do not have a file inside the home partition, if I need to change its format, it is not a problem.

---

### Post by TheFu on 2021-07-16
The file system used doesn't matter.

Does Windows stop the HDD when it isn't being used?  You can do the same with **hdparm** on Linux, if the drive supports that.  This should reduce power consumption at the cost of slower access times when the drive has to spin up.

Laptops often have cooling issues.  The solution is to clean away any dust from inside, keep the fans clear so they can move air, and don't close the lid, since radiant cooling up through the keyboard is almost always part of the thermal design in laptops.

I can't help you with your Win10 problem. Sorry.

---

