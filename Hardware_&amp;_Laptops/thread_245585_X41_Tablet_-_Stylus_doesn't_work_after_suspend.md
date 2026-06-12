---
title: "X41 Tablet - Stylus doesn't work after suspend"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by kderose on 2006-08-28
Hello!

I have an ibm x41 tablet and the stylus seems to be working fine with some lines added to my xorg.conf file except that after I suspend the computer it stops working.  Once I restart the computer it is back to normal, but for some reason the suspend kills it.  Any suggestions?  Thanks!!!

-Kim

---

### Post by shazow on 2006-09-03
Hi there,

I have the same problem (albeit not on Ubuntu, but on Gentoo). Please post back here if you figure it out? 

Thanks,
- shazow

---

### Post by kderose on 2006-09-04
Do you have ibm-acpi installed?  I couldn't find this package in the synaptic package manager so I've been trying to manually install it with little success.  I keep trying to type the command "make" but despite the fact that I've downloaded the build-essential package I do not seem to have the file necessary (it is looking for a directory called "build" that doesn't seem to exist).  I think ibm-acpi might have the code needed to make it work...but as I can't get this install to work, there is no way to check.  Any suggestions?

---

### Post by bencorrado on 2006-09-10
Run
# setserial /dev/ttyS0 port 0x0200 irq 5 autoconfig

after resume

You can also add this to the resume script in /etc/acpi

---

### Post by kderose on 2006-09-11
My wacom stylus is currently using /dev/ttyS4, but when I feed it the command  /dev/ttyS4 port 0x0200 irq 5 autoconfig I get the response "Cannot set serial info: Device or resource busy".  And the stylus refuses to work...

Any suggestions?  

Thank you so much for your help!

---

### Post by ecoxmit on 2006-10-22
I am having exactly the same problem with my X41 tablet: the pen stops working after resuming from suspend or hibernation. 

I also tried the suggestion above, but it didn't work. 

other suggestions?

---

### Post by pet22 on 2006-10-31
Hi all,

This is the solution which I used:

although the command "setserial /dev/ttyS0 port 0x0200 irq 5 autoconfig" does not work in X it does in a console mode. Which means that after susspend you can restore tablet functionality. (for beginners: to change to a console by pressing ctr+alt+F1 or any F up to 6 than when you come back to X by pressing alt+F7)

To make it an automatic service you have to do what fallows. Create a file in /etc/acpi/resume.d/ with a .sh extension an a low number in the folder so it is executed early in resume process.

If you do not wish to understand this you are very welcome, those are the commands I've executed:

sudo vi /etc/acpi/resume.d/11-x41-wacom.sh

I added to the created file:

#!/bin/sh
setserial /dev/ttyS0 port 0x0200 irq 5 autoconfig

finaly, I had to libareta some rights:

chmod +x /etc/acpi/resume.d/11-x41-wacom.sh

AND IT WORKS :) 

Good luck to all of you Linux savy people,

Piotr

PS. This is way to long, sorry

---

### Post by freund on 2007-05-25
Thanks. Solution works great on my X60.
Had to get "setserial" first since it wasn't installed. 
Thanks again.
al

---

