---
title: "Dual boot Windows 7 and Ubuntu with 2 hard drives"
date: 2014-11-27
forum: Hardware
---

### Post by cgameing on 2014-11-27
So I Want to dual boot Windows 7 and Ubuntu with 2 hard drives.
Both hard drives has a os installed (1 ubuntu 14.04 lts the other windows 7)

When i only have 1 hard drive installed on my pc it boots that hard drives OS

When i have both installed it chooses a random OS or errors.
When i say errors the BIOS (Asus UEFI bios) says overclocking failed (i have overclocked my AMD A6-6400k recently).

Any help is much apreciated.

---

### Post by oldfred on 2014-11-27
Post link to summary report so we can see details. Do not run autofix.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Reha_Andrew on 2014-11-28
While installing ubuntu they will ask you installation type choose "something else" option. Advanced Partitioning Tool&#8217;s window will get open. Remember both HD should be labeled as /dev/sda and /dev/sdb. Do not touch windows 7 HD AND click on the button free space and start creating partitions.

---

### Post by cgameing on 2014-11-28
Reha_Andrew i already have installed both so i couldent partition it.

And ubuntu wont detect it anyway so i cant partition it after i installed it (even with a usb as the OS)

---

### Post by cgameing on 2014-11-28
boot repair doesnt work

---

### Post by yancek on 2014-11-28
> boot repair doesnt work 		

Yes it does.  In fact there are hundreds of posts here at this forum with the output of the boot repair script.  If you mean you cannot get it to work then you will need to post some information on what you did so someone can point out your error.   You need to post some details on your system.  When you installed Ubuntu, did you have the windows drive attached?  Did you run sudo update-grub after installing Ubuntu?  The link below explains how to use boot repair so you might read that to find out what is going wrong.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cgameing on 2014-11-28
Both drives attached ran boot repair and no improvements or errors detected
I suspect my power supply cant handel the 2 harddrives (with internet card graphics card and other stuffs)

---

### Post by yancek on 2014-11-28
I've never used boot repair but from what I understand from reading numerous posts here, there is an option to get a summary report without attempting to do any repairs which includes a lot of detailed information on your system.  That is what oldfred asked you for in his post above and would help someone here to help you.

---

### Post by Mark Phelps on 2014-11-29
> I suspect my power supply cant handel the 2 harddrivesUnless you're running some low-end PSU like 200 watts, I seriously doubt that two hard drives are going to tax your PSU very much.  The high-end graphics cards tend to tax PSUs the most, as many require 500 watt PSUs to work properly.

---

### Post by cgameing on 2014-12-04
yea 320 watt power supply is problem

---

### Post by cgameing on 2014-12-04
how do i set this to solved

---

### Post by mörgæs on 2014-12-04
Please use Thread Tools.

---

### Post by cgameing on 2014-12-05
how to set thread to solved

---

### Post by oldfred on 2014-12-05
More info on closed.

[http://ubuntuforums.org/showthread.php?t=2054969&p=12237427#post12237427](http://ubuntuforums.org/showthread.php?t=2054969&p=12237427#post12237427)

---

