---
title: "HP Laptop Start up Issue"
date: 2009-09-09
forum: Hardware
---

### Post by winstont11 on 2009-09-09
I have a HP laptop computer and its not working properly for me.

Its a dual boot between ubuntu and microsoft xp home edition and I have the same issue whenever I try to access ubuntu or microsoft.

Uncompressing Linux... Ok, booting the kernel.
[17179570.936000] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[17179570.936000] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[17179599.400000] hda: timeout waiting for DMA
[17179604.404000] hda: drive not ready for command
[17179639.408000] hda: drive not ready for command


When I try to log into microsoft it just sits at the startup screen
and then it wont go anywhere.. I'm not sure whats wrong or what I should do to figure it out.  I'm extremely novice when it comes to computers so please be patient : ) I appreciate the help

---

### Post by haxer on 2009-09-09
Hda is primer hdd so some problem with that and the pci of course.

---

### Post by winstont11 on 2009-09-09
Any recommendations on how to fix this problem?

---

### Post by winstont11 on 2009-09-10
I was told that I may need to get a new hard drive, but I'm not sure.  If theres a way to correct this problem without having to get a new hard drive I'd like to try that first.

---

### Post by Zimmer on 2009-09-10
> **winstont11 said:**
> I was told that I may need to get a new hard drive, but I'm not sure.  If theres a way to correct this problem without having to get a new hard drive I'd like to try that first.

Have a look at the Troubleshooting Section here:

[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

regarding the [Cable Select] Master/ Slave settings on the drive.

Might just be a loose connection, too. (In the hope that your drive is not failing!!) 

Can you see and mount the partitions using the LiveCD ?

---

