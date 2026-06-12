---
title: "Cannot mount another hard disk in Ubuntu 18.04!"
date: 2019-02-02
forum: Hardware
---

### Post by farewell97 on 2019-02-02
Hi everyone,
I'm using Ubuntu 18.04 and dual boot with win10. I can mount the partition of win 10 in the same hard disk, but 2 partitions of another hard disk are not, it's NTFS.
I tried to fix a lot but nothing work. Thanks for your help.
This is boot-info log:
[http://paste.ubuntu.com/p/H6P4wS9QVX/](http://paste.ubuntu.com/p/H6P4wS9QVX/)

---

### Post by yancek on 2019-02-02
What happens when you run the commands suggested by boot repair on the specific partitions, sda1 and sda2?

> NTFS is either inconsistent, or there is a hardware fault, or it's aSoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. 

---

### Post by farewell97 on 2019-02-02
It says Windows found no problem and no further action is required, above of sda1 and sda2.

---

### Post by vanadium on 2019-02-02
Check the ntfs disk in MS Windows using either chkfs /f or the graphical tools. Make sure Windows is fully shut down (no hibernate). The output you post even suggests rebooting into Windows twice (and shutting down fully each time). If these conditions are fulfilled, the disk will mount.

---

### Post by farewell97 on 2019-02-02
> **vanadium said:**
> Check the ntfs disk in MS Windows using either chkfs /f or the graphical tools. Make sure Windows is fully shut down (no hibernate). The output you post even suggests rebooting into Windows twice (and shutting down fully each time). If these conditions are fulfilled, the disk will mount.
I'm sure I did all of them but still not woking.

---

### Post by coffeecat on 2019-02-02
Merely sure or absolutely certain?

The advice to ensure Windows is fully shut down and not hibernated means that you must have disabled fast startup in Windows. If you haven't, it doesn't shut down properly. Have a look at this link, especially the bullet points under "Why You Might Want to Disable Fast Startup", and the how to section below that if you need to know how to disable fast startup.

[https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/](https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/)

---

### Post by farewell97 on 2019-02-02
> **coffeecat said:**
> Merely sure or absolutely certain?

The advice to ensure Windows is fully shut down and not hibernated means that you must have disabled fast startup in Windows. If you haven't, it doesn't shut down properly. Have a look at this link, especially the bullet points under "Why You Might Want to Disable Fast Startup", and the how to section below that if you need to know how to disable fast startup.

[https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/](https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/)
[IMG]https://i.imgur.com/CsiVITM.png[/IMG]
Is this right? I dit it right after installing Ubuntu.
[IMG]https://www.flickr.com/photos/167115027@N08/46906913152/in/dateposted-public/[/IMG][IMG]https://flic.kr/p/2et1c4W[/IMG]

---

### Post by farewell97 on 2019-02-03
Thank you guys for helping me. I've just formatted and then it's mounted. :lolflag:

---

