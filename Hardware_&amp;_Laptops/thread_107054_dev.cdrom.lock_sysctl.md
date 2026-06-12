---
title: "dev.cdrom.lock sysctl"
date: 2005-12-22
forum: Hardware &amp; Laptops
---

### Post by Grey on 2005-12-22
Hi.  I was reading this [bug](https://bugzilla.ubuntu.com/show_bug.cgi?id=11480), and the solution to the problem I want to solve (using the eject button to eject a CD), is to modify the dev.cdrom sysctl.  This works just fine if I use it from the command line... but the permanent fix is to modify the /etc/sysctl.conf file... which is supposed to be read at boot.

I have this line in my sysctl.conf:

dev.cdrom.lock=0

Which, is the same as I use from the command line.  But it gives me an error on boot that the sysctl is not recognized.  I am thinking that it's loading the configuration file before initializing the CD-ROM... but I have no idea how to go about fixing that.

Help?

---

### Post by Grey on 2005-12-30
bump?

Someone has to know how this works, right?

---

### Post by abovett on 2005-12-30
I can't help I'm afraid. You may have more luck joining in the discussion on Bugzilla - if you have actually found a problem with a solution proposed there then it may be useful input for the devs.

Andy B

---

