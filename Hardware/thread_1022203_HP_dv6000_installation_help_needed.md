---
title: "HP dv6000 installation help needed"
date: 2008-12-26
forum: Hardware
---

### Post by edpatterson on 2008-12-26
HP Pavilion Entertainment PC (dv6000 laptop)

I know it will work, I just do know know enough about Linux to make it do so.

I bought the laptop the first day Vista went on sale and have had nothing but problems ever since. I am lucky if I get 4 months usage before I have to wipe the drive and reinstall.

I booted it with a Live CD, entered my WEP key and life was good. I could cruise the Internet, browse my existing files and anything else I tried. So I figured I would buy a new drive, install XP then install Ubuntu and dual boot the machine.

The XP install worked even though none of the peripherals were recognized (expected behavior). Then I booted from the Live CD, repartitioned the HDD and installed Ubuntu. Ubunu did not recognize and of the peripherals (not expected behavior).

I then tried to boot to XP and install the drivers thinking that Ubuntu might magically read the XP pretition, see the configuration and somehow figure out what was on the machine. XP blue screened complaining about invalid boot media or come such foolishness. Much reading later I decided that I really did not need XP on the machine anyway.

PHEW

What steps should I take to wipe all of the partitions from the drive and ensure the chipset, video, audio, and network controllers are recognized.

Thanks for any assistance
Ed

---

### Post by albandy on 2008-12-26
I have a dv6000 too, exactly a dv 6745es and all works perfect.
I've installed ubuntu 8.10 and VirtualBox to run other OS (including Windows XP).

If you want to complete delete all partitions of your hard disk open a console and type:
"sudo fdisk /dev/sda"
then type "p" to list all your partitions
then type "d" and type the number of partition you wish to delete
type "d" to every partition you want to delete
finally type "w" to save the changes.

After this reboot your computer with the ubuntu CD and install it.
Upgrade the system and now your computer is ready to work.

If you want to run other Operative Systems install VirtualBox.

---

### Post by edpatterson on 2008-12-26
Thanks, I was able to delete the partitions and install Ubuntu. Matter of fact I am using the laptop right now!

Ed

---

### Post by rca219 on 2008-12-26
> **edpatterson said:**
> Thanks, I was able to delete the partitions and install Ubuntu. Matter of fact I am using the laptop right now!

Ed
Do you have any audio problems - do the speakers work properly?

---

