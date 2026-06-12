---
title: "My external hard disk doesn't work under Ubuntu"
date: 2009-10-13
forum: Hardware
---

### Post by Shotokax on 2009-10-13
Hello everybody.

I've surfed a lot in the Internet but I can't find any solution to my problem. Any help will be very wellcome.

I've an USB external hard disk. Its model is Western Digital WD2500E1MS (250 GB). When I plug it in my PC Ubuntu doesn't do anything and its file system is not mounted in /media or any other directory as far as I know.

Can you help me, please?

Thank you very much in advance.

---

### Post by Shotokax on 2009-10-13
Sorry. I've forgotten to say that WD's official website says that this model is supported for Mac and Windows and there are no available drivers (even for Mac and Windows).

Do you think I can do anything?

Thank you again.

---

### Post by arrange on 2009-10-13
We need more info - disconnect the drive, wait a few seconds, and connect it back again. After a while open the [Terminal](https://help.ubuntu.com/community/GnomeTerminal) and [copy](https://help.ubuntu.com/community/UsingTheTerminal#Pasting%20in%20commands) these commands into it```
dmesg | tail -20
lsusb
sudo fdisk -l
```Then copy the output here (log, usb devices list, partitions list).

---

### Post by Shotokax on 2009-10-13
I'm sorry. The problem was in the USB cable and I've been able to resolve it.

Thank you very much anyway.

---

