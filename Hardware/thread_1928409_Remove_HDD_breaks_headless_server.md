---
title: "Remove HDD breaks headless server"
date: 2012-02-20
forum: Hardware
---

### Post by mikulator on 2012-02-20
I have a headless machine (running myhtbuntu) with several HDD installed.

Physically removing a non OS drive breaks the server so much that I cannot connect to it via VNC.

The issue concerns me because I suspect a defect HDD would also prevent me from connecting.

I could of course use RAID, for various reasons I choose not to.


This leeds to the following questions

  
1) what is the be way to remove the drive and not breaking the system?
2) what preventive actions (other than RAID) can I implement?

Cheers

---

### Post by MartyBuntu on 2012-02-20
I wonder if logging in to your machine, deleting the **fstab** file and then sending the shutdown command, followed by removing the drive would work. Logically, a new **fstab** file should be rebuilt when you boot up again.

---

### Post by mikulator on 2012-02-20
I suspect you are right, but I don't know if I have the nerves to do that.

I also agree that it is most likely that it is fstab that gives the error preventing the proper boot.

Cheers

---

### Post by MartyBuntu on 2012-02-20
I've done this before to cure fussy GRUB issues.

Of course, you could always backup your **fstab** file and restore it later, if you need.

---

### Post by mikulator on 2012-02-20
well the problem is if I break the server the I see nothing and will have the task of booting form CD/USB and restoring fstab.

---

