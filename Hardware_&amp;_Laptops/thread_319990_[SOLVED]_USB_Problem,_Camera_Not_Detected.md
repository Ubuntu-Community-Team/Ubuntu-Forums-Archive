---
title: "[SOLVED] USB Problem, Camera Not Detected"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by Simon G Best on 2006-12-16
Hello!

Just this last week, I've installed Xubuntu 6.10 (Edgy Eft).  I've had various problems, but am generally getting them solved (or, at least, 'solved').  One of the remaining problems is that my USB camera isn't getting detected when I plug it in and switch it on.

The camera is a Kodak EasyShare CX6200.  From what I remember, it uses PTP (which was one of the reasons I bought it when I did).  It used to work with gphoto2 when I was using RedHat 7.2, and vaguely worked when I was using RedHat 9.  Now it's not working at all.

I've had a look at lsusb and dmesg, to see if plugging it in and/or switching it on makes any noticeable difference there, but nothing gets reported.  I think it's some sort of USB problem, as lsusb doesn't mention my printer, either, even though it's plugged in and switched on.  (I haven't tried to get printing going, yet.)

Any ideas?

:)

---

### Post by rutger83 on 2006-12-27
Same problem here. It's a general Edgy problem for me: no USB devices at all. And my dapper recognizes everything....

---

### Post by ro-tex on 2007-01-03
I have a strange USB problem, too. Before upgrading from Dapper to Edgy my USBs worked fine. Now when I attach a device nothing happens. No /dev/sd*, no reaction, no entry in the dmesg or syslog... Nothing. I tried connecting my card reader and my ipod. The funny thing is there is power on the ports, so I can charge my ipod without a problem but it reacts as if I connected it to an electrical socket - just charging without warning me that it's connected to a computer.

On the other hand my colleague upgraded his Dapper to Edgy and did not experience this problem - both my card reader and ipod start off smoothly on his machine...

Oh, and the same goes for my Canon A630 camera...

---

### Post by pengwern on 2007-01-05
> **ro-tex said:**
> The funny thing is there is power on the ports, so I can charge my ipod without a problem but it reacts as if I connected it to an electrical socket - just charging without warning me that it's connected to a computer.
Ro-tex,

I had exactly the same problem.  What worked for me was putting the ipod into "disk mode" and it's now firing on all cylinders.  I've even got an "Ipod" icon on my gnome desktop, which allows me to "umount" the device gracefully, and Rhythmbox pops up automatically so that I can edit/add new tracks.

Instructions for "disk mode" at [http://docs.info.apple.com/article.html?artnum=93651](http://docs.info.apple.com/article.html?artnum=93651)

---

### Post by ro-tex on 2007-01-05
Well, no icon on my desktop, but the ipod mounts without any problems. Thanks! :)

---

### Post by bexpert on 2007-02-27
Any solutions for the cameras? I can't get my A630 to show up--although I don't really know what I'm doing.

 My A75 works fine in digiKam. My A630 is seen, but no files can be detected.

---

### Post by Simon G Best on 2007-05-11
I've finally solved my USB problem: [http://ubuntuforums.org/showthread.php?t=373613](http://ubuntuforums.org/showthread.php?t=373613)

My camera is now working with my Feisty PC :)

---

