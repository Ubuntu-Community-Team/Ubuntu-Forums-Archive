---
title: "Universal Power Supply System ? Server ?"
date: 2008-11-18
forum: General Help
---

### Post by UltraDangerLord on 2008-11-18
Hello All,

I'm looking for a few ideas or some guidance with a UPS server of some sort.

The Problem:

We have about 4 servers, 2 routers and 2 firewalls running on 3 UPS boxes from tripplite. 

The tripplite UPS boxes come with a software to talk to a windows machine via a usb or serial port.

Problem is theres only 1 windows machine and the other 3 are freebsd / ubuntu.

So, when the power goes out on the machines they start to pull from the battery until it dies.

I need some way to regulate and shut these systems off so they don't get damaged... any ideas ?

-Thanks

---

### Post by dcstar on 2008-11-19
> **UltraDangerLord said:**
> 
......
I need some way to regulate and shut these systems off so they don't get damaged... any ideas ?

-Thanks

You either need Linux software from the UPS vendor, or find a new UPS that supports Linux.

At work I have a Powerware UPS connected to a Windows box, and other Windows and AIX boxes run software that controls them from the connected Windows machine (they are all powered by the one UPS).

---

