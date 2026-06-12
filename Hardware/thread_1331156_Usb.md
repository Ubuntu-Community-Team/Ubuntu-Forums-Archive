---
title: "Usb"
date: 2009-11-19
forum: Hardware
---

### Post by iondb on 2009-11-19
Hi there all.  I am new here,  and also new to Linux and Ubuntu.

I seem to have a problem on my PC, I can't get any USB devices to work on Ubuntu? USB keyboard, mouse and usb memory stick does not work when connected.

---

### Post by emigrant on 2009-11-19
past output for:

```

lsusb

```

---

### Post by iondb on 2009-11-19
Like I mentioned, don't know too much about Linux, but this is what I got from a terminal

   gerrit@gerrit-desktop:~$ lsusb
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  gerrit@gerrit-desktop:~$

---

### Post by iondb on 2009-11-20
Any news on this?

---

### Post by emigrant on 2009-11-20
go to synaptic package manager and see whether you have installed:
pciutils

---

### Post by coffeecat on 2009-11-20
Have a look in your BIOS. It could be that you need to enable USB support there - particularly if this is an older machine.

---

### Post by iondb on 2009-11-20
Thanks for the replies.  Yes, the USB is installed/enabled in the BIOS.

Nope no pciutils installed???

---

### Post by emigrant on 2009-11-20
Install it.

---

