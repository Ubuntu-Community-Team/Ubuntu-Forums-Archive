---
title: "USB Hell"
date: 2008-05-18
forum: Hardware
---

### Post by KitchenKnif on 2008-05-18
My desktop pc has four USB ports - Two on the front & two on the back. I know they all work, both from when I had Windows installed & because my external HDD works on the two front ports, and my printer from the two back ports.
All is well...Until I need to copy files from my external HDD to a flash drive. I connect ANY flash drive (tested 4) to one of the ports in the back, and I can see it in Nautilus, through fdisk -l and everything. But when I try to open it...It either doesn't work at all or starts spewing I/O Read-Write errors and gets reset, and starts all over.
And all those drives work perfectly on the two front ports, and everywhere else...Just not on the back ports?
Any ideas?

---

### Post by nicedude on 2008-05-18
Hi sorry to hear you are having problems you could try the following command to list your USB devices the system recognizes.

First you can update the list itself so that you have the most up to date list in your system for it to list your drives correctly

Command to update USB deivce list
sudo update-usbids 

Command to list USB devices detected by Ubuntu in your system
lsusb

Please post the results of lsusb with several of your drives connected and I will try to see what the problem is, If I can't it will give someone else wiser than I a better understanding of your problem.

Also please try to give any errors you are seeing so someone can diagnose that as well.

nicedude

---

### Post by KitchenKnif on 2008-05-18
drwatson@RustyDesktop:~$ sudo lsusb
Bus 004 Device 025: ID 041e:4120 Creative Technology, Ltd 
Bus 004 Device 024: ID 3538:0054 Power Quotient International Co., Ltd 
Bus 004 Device 023: ID 067b:2507 Prolific Technology, Inc. PL2507 Hi-speed USB to IDE bridge controller
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

This is what i get with my external HDD on the two fronts ports,
and my Creative MuVo & and a 2gb flash drive on the back ports.

As for the errors... strangely - this time, everything works perfectly...

---

