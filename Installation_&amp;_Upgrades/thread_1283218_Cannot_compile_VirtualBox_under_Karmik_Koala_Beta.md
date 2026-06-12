---
title: "Cannot compile VirtualBox under Karmik Koala Beta"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by vbulash on 2009-10-05
Attempt to install VirtualBox Guest Additions for newly installed in virtual machine Koala guest (host = Ubuntu 9.04) produces the following output:

```
Verifying archive integrity... All good.
Uncompressing VirtualBox 2.2.4 Guest Additions for Linux installation..............................................................................................................................................................................................................................
VirtualBox 2.2.4 Guest Additions installation
Building the VirtualBox Guest Additions kernel module...
Building the shared folder support kernel module...
Unable to build the kernel module.  See the log file /var/log/vboxadd-install.log
for more details.
```

Both systems - host / guest - has x86 architecture.
Log file attached here as an archive.
What's wrong? Is it a real bug in beta version of Ubuntu 9.10 or something else?

---

### Post by renkinjutsu on 2009-10-05
seems like it failed at building kernel modules..
this usually means you haven't installed your kernel headers yet
to get them:
```
sudo aptitude install linux-headers-2.6.31-11-generic
```

---

### Post by vbulash on 2009-10-05
> **renkinjutsu said:**
> seems like it failed at building kernel modules..
this usually means you haven't installed your kernel headers yet
to get them:
```
sudo aptitude install linux-headers-2.6.31-11-generic
```

No. Synaptic show me that this package already installed.

---

### Post by vbulash on 2009-10-05
> **vbulash said:**
> No. Synaptic show me that this package already installed.

It is a Sun VirtualBox bug - [http://www.virtualbox.org/ticket/4823](http://www.virtualbox.org/ticket/4823)
Now I'll try to use latest virtualbox from its repository

---

### Post by doomsword2001 on 2009-10-05
the repository version (OSE) has a problem with usb. better download it from official website v3 i think

---

### Post by vbulash on 2009-10-06
> **doomsword2001 said:**
> the repository version (OSE) has a problem with usb. better download it from official website v3 i think

Agree.
Just 3.0.6 version fully support Koala guest because of implemented support of 2.26.31+ core.

---

