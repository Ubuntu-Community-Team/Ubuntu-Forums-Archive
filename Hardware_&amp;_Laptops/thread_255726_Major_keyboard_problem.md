---
title: "Major keyboard problem"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by TheMatt on 2006-09-11
[SIZE=2]While I was working today, the keyboard suddenly stopped responding. It wouldn't work for any program, so I rebooted. Still nothing. I notice that I can use the keyboard to select linux at boot and I can use it to log into linux, but beyond that it is useless. I am stumped. I would really like it back because I have some important files on my ext3 partition that I need, Please help![/SIZE]

---

### Post by ruedu on 2006-09-11
Try a different keyboard, such as a usb one so you can reconfigure things.

---

### Post by TheMatt on 2006-09-12
I am going to borrow a USB keyboard today. what should I reconfiggure?

---

### Post by Timothy Butwinick on 2006-09-12
There are some options in the /etc/X11/xorg.conf file for keyboards. Maybe these have been altered? Of course, it's hard to change them without means of typing, but if you get the USB-keyboard to work, you should check the file.

---

### Post by TheMatt on 2006-09-12
Got it:
[http://www.linuxquestions.org/questions/showthread.php?t=470019](http://www.linuxquestions.org/questions/showthread.php?t=470019)

---

