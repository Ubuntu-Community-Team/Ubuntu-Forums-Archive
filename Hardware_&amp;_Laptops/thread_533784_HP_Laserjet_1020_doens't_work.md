---
title: "HP Laserjet 1020 doens't work"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by chadrlz on 2007-08-24
I am using Ubuntu 7.10 and I recently got a HP Laserjet 1020 and I can not get it to work. I have tried all sorts of things but have not had any luck.I have tried CUPS, and the foo2zjs driver. I really need to have this thing working sooner than later.

---

### Post by w4ett on 2007-08-24
Here's a link for a successful install of that printer in Ubuntu:

[http://20six.co.uk/jabolins/art/14803150](http://20six.co.uk/jabolins/art/14803150)

---

### Post by chadrlz on 2007-08-24
Oh K. I used the link below which did solve my original problem.

[http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/](http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/)

The new problem is that I can't print out of a terminal client. This is a real problem because this printer has to be used with terminal services to print from within a windows comp through terminal services.

---

### Post by trixon on 2007-10-19
Great, now I got my HP 1020 working in Kubuntu 7.10.

---

### Post by potentia on 2007-10-19
> **chadrlz said:**
> Oh K. I used the link below which did solve my original problem.

[http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/](http://stepien.com.pl/2006/09/23/install-your-hp-laserjet-1020-on-ubuntu/)

The new problem is that I can't print out of a terminal client. This is a real problem because this printer has to be used with terminal services to print from within a windows comp through terminal services.


Yep, this one works.

---

### Post by suoko on 2007-10-21
I have a problem with this printer too.
By following stepien instructions it works but after a reboot, if I try to print all jobs are put on-hold-until-specified.
In order to start printing I have to unplug and replug the printer.
What's the problem here?

<SOLVED>
In the system-config-printer gui I set printer URI to HPLIP instead of HAL.

---

### Post by potentia on 2007-10-21
> **suoko said:**
> I have a problem with this printer too.
<SOLVED>
In the system-config-printer gui I set printer URI to HPLIP instead of HAL.


Exactly where, please?

My URI says "usb://HP/LaserJet%201020"

---

