---
title: "Disk monitor program?"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by XoRDy on 2006-05-10
Hi,

I manage an local Web(samba/php/mysql) server and quite now it's very slow, we are 10 employees and we access to the server throght an 100mb ethernet card, it has an SCSI 160 disk (only 40MBYTES/s)

I run top, and I see that the maximum cpu usage is 20%, good
I top, I see that I've got 160MB of free RAM, good
I install and run bwm and I see the average usage of the NIC is less than 1MByte, good

Then I thought it must be the hard disk.. How can I monitor the usage (#access/sec and MB/sec) of the hard discs??

Greetings.

---

### Post by mjm115 on 2006-05-10
apt-get install gnome-applets

[gnome-applets]("http://packages.ubuntulinux.org/breezy/gnome/gnome-applets") contains the System monitor aplet that allows you to monitor your CPU, memory, network, swap file and resources

---

### Post by XoRDy on 2006-05-10
I need an text-based program, is there any?

thanks!!

---

### Post by XoRDy on 2006-05-11
Pleas, I need one in text mode, does somebody know?


please

---

### Post by mips on 2006-05-11
Have a look at iostat, xiostat, hdparm, smartmontools. I think (x)iostat might do what you need.

[http://www.tldp.org/HOWTO/SCSI-2.4-HOWTO/perform.html](http://www.tldp.org/HOWTO/SCSI-2.4-HOWTO/perform.html)    maybe there is some usefull stuff in there

---

### Post by XoRDy on 2006-05-12
Thanks for your help, that's more or less what I was looking for, it would serve.

:P

Greetings

---

