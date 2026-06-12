---
title: "APC UPS Program?"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by CarlosinFL on 2007-03-29
I have an APC UPS which has a data port on the UPS unit and it connects to  my PC via UPS. I see that I found some programs via APT but I am not sure which would be the correct program to install. I am sure I could try them all but I would rather ask 1st and install the correct one.

The APC UPS I am using is Back-Ups ES 500 / which also doubles as a surge protector as well as a home/office UPS.

Here is what I find in APT:

```
root@tank:~# apt-cache search apc
apcd - APC Smart UPS daemon
apcupsd - APC UPS Power Management
apcupsd-cgi - Cgi for APC UPS Power Management
apcupsd-doc - Documentation for apcupsd

```

Any suggestions?

---

### Post by cyberdork33 on 2007-03-29
I think apcupsd is the most popular... It is just a daemon though, there is no nifty gui like the windows APC software.

---

### Post by CarlosinFL on 2007-03-29
> **cyberdork33 said:**
> I think apcupsd is the most popular... It is just a daemon though, there is no nifty gui like the windows APC software.

So what will the Daemon do if I install it? I was really wanting some kind of GUI but as you noted - that is not what is noted by my find results in APT. So I guess I don't know why I should bother installed in the daemon.

---

