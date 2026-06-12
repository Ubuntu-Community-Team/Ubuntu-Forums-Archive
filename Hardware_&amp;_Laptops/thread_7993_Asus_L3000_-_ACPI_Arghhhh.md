---
title: "Asus L3000 - ACPI Arghhhh"
date: 2004-12-13
forum: Hardware &amp; Laptops
---

### Post by lyahgelo on 2004-12-13
My ACPI on ASUS L3000 don't work..
Have I to use APM?
When I modprobe apm it doesn't work...
What can I do?
 :-&

---

### Post by lyahgelo on 2004-12-14
What about acpi4linux?
Does someone know if this is available for ubuntu? Is there the debian package?

---

### Post by spider7378 on 2005-02-10
Hi! I have the same problem! I can only boot Ubuntu when turning ACPI off.  :?

---

### Post by keeee on 2005-02-10
This solution worked for me --> Asus L3000D:
Get the 2.6.10 kernel and install it. Easiest way is via backport system: [kernel 2.6.10 thread](http://ubuntuforums.org/showthread.php?t=12581) 

In short:
1) add following lines in your /etc/apt/sources.list
deb [http://cloud9.somniumcomputing.com:81/ubuntu/backports](http://cloud9.somniumcomputing.com:81/ubuntu/backports) warty-backports main universe restricted
deb [http://cloud9.somniumcomputing.com:81/ubuntu/backports](http://cloud9.somniumcomputing.com:81/ubuntu/backports) warty-backports-staging main universe restricted

2) apt-get install linux-image-2.6.10-2-k7 (if you have an amd processor)

3) add acpi=on instead of acpi=off in your grub configuration ( /boot/grub/menu.lst )

It's still far from complete, but at least battery info and powerbutton work. CPU throttling or sleep/hybernate doesn't work yet, I'll look for it soon.

---

