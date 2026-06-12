---
title: "scsi scanner requires root"
date: 2009-11-15
forum: Hardware
---

### Post by satbunny on 2009-11-15
My SCSI scanner requires root to run since the scanner is at
Quote:
/dev/sg2
and everytime I reboot it resets the permissions.

Is there an elegant solution to prevent the need to keep resetting the permissions or running as root?

I have read the threads re USB scanners and looked in
Quote:
/lib/udev/rules.d/50-udev-default.rules
but the only scsi devices in there seem to be disks and cdroms..

---

### Post by SuperSonic4 on 2009-11-15
Have you tried adding yourself to the scanner group?

```
sudo gpasswd -a *username* scanner
```

Where username is your username

---

### Post by satbunny on 2009-11-15
I am a member of the scanner group..

---

### Post by satbunny on 2009-11-16
I have noticed that the libsane-extras package (1.0.19.11) in jaunty has the following listed as an installed file:


/lib/udev/rules.d/40-libsane-extras.rules

It is installed, but elsewhere people talk of this file being in /etc/udev/rules.d

Could this be the problem?

---

### Post by satbunny on 2009-11-20
SOLVED:

Using the guide here: 

[http://jhansonxi.blogspot.com/2009/08/writing-udev-rules-to-get-scsi-scanner.html]("http://jhansonxi.blogspot.com/2009/08/writing-udev-rules-to-get-scsi-scanner.html")

---

