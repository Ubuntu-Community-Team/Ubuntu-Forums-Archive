---
title: "Keyboard And Mouse problem"
date: 2009-04-30
forum: Hardware
---

### Post by daimonas on 2009-04-30
Hi all. This my first post in linux forums. Plz help.
I have a Microsoft Wireless Comfort Keyboard 1.0A and i Wireless Optical Mouse 2.0A and an asus p5ad2-e mobo. Both are working with one USB slot.I was happy with ubuntu 8.10. Everything worked fine after upgrading to 9.04 the keyboard and mouse stopped working since boot. I can see the reciever light flashing for 1 second and 1 second not.Its like mounting and unmounting the device every one sec.Keyboard works fine before linux boots. Tried all the usb ports. Im now typing with a wired usb keyb that works fine. Keyboard works fine under vista.Then i thought that i need a clean installation of 9.04 but keyb and mouse are not recognised any more from ubuntu 9.04 setup.Besides that i finished the installation with the wired keyboard and i don't know what else to do. thanx in advance and sorry about my english

---

### Post by dtom2444 on 2009-04-30
sounds like a drivers issue. this happens a lot with new updates, "old" stuff stops working. try looking on the Microsoft website for any newly released drivers (although i doubt they would support Ubuntu like that). if all else fails, try the Ubuntu IRC channel #Ubuntu.

---

### Post by Nagy on 2009-05-18
Yes, I am having the same issue. It actually is a kernel version problem: I compiled and installed 2.6.29 under 8.10 and both the mouse and keyboard stopped working. Maybe compiling a 2.6.27 kernel and installing it under jaunty will solve the problem.

---

### Post by hazylunarrain on 2009-05-21
:popcorn:

I also have this issue. I will stick to 8.1 until a workaround is found, but I wouuld really liek to make the switch.

---

### Post by Gen2ly on 2009-05-21
Hmm, don't see how this could be a kernel issue.  Likely this has to do with xorg server 1.6 and the new hotplugging.  I haven't  had issues with it but you can find out more about it here:

[http://wiki.archlinux.org/index.php/Xorg_input_hotplugging](http://wiki.archlinux.org/index.php/Xorg_input_hotplugging)

A lot to read but it's a good guide.

---

