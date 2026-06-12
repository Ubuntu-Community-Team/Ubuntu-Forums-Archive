---
title: "Can't sync my Sony Clie Palm"
date: 2008-09-10
forum: General Help
---

### Post by forrestcupp on 2008-09-10
I'm using an updated version of Intrepid.  I'm trying to get an old Sony Clie NX70V to sync, and I'm not having any luck setting it up.  I can tell that Ubuntu *is* recognizing the Clie, but I can't get it to connect.

Here is the output of lsusb while the hotsync button is pressed:

```
Bus 006 Device 007: ID 054c:00da Sony Corp. Sony Clie nx60
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c20b Logitech, Inc. WingMan Action Pad
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 04ca:0020 Lite-On Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```So you can see the Clie on the first line being recognized.  It just won't connect to Gnome Pilot.

I realized that the Palm rule in /etc/udev/rules.d/60-symlinks.rules wasn't creating the symlink called /dev/pilot.  I found a fix for that [here](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg09355.html).  So I commented out that rule and put the following in its place:
```
KERNEL=="ttyUSB*", SYSFS{product}=="*Palm*", \
					SYMLINK+="pilot"
```

Now it successfully creates the pilot symlink whenever I press the hotsync button.  But it still is not connecting to Gnome Pilot.  It just keeps trying to connect until it finally times out.  That is using the USB option.

I am using the visor module.  I had to modprobe visor because I saw that starting with Gutsy, it's not loaded by default.  

Does anyone have any ideas on how I can get this thing connected?

---

### Post by forrestcupp on 2008-09-13
Nobody has any ideas on this?

---

### Post by Nizarus on 2008-10-12
I have the same issue with my clie
the device is recognised by the system (lsus) but not recognised by gpilot !!

---

