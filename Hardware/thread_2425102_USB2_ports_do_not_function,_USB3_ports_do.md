---
title: "USB2 ports do not function, USB3 ports do"
date: 2019-08-20
forum: Hardware
---

### Post by artist-wavenet on 2019-08-20
I have on my computer case 3 USB 3.0 Ports, and 9 USB2 ports. All the USB 3.0 ports work with everything as expected, but none of the USB 2.0 ports do. Those USB 2.0 ports do not work with my keyboard, mouse, printer, or USB drives. I do not know if this is a hardware failure, or a bad driver installation.

OS: Ubuntu 18.04
Motherboard: Gigabyte 970A-D3P

Some diagnostic commands, and their outputs, with a USB Drive plugged into a USB2 port:
```

n@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 005: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 008 Device 004: ID 1e7d:2e7c ROCCAT 
Bus 008 Device 003: ID 03f0:6412 Hewlett-Packard 
Bus 008 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
n@ubuntu:~$ ls /dev/ | grep sd
sda
sda1
sda2
sda3
sda4
sdb
sdb1
sdb2
sdb3
sdb4

```
sda and sdb are RAIDed together in a RAID1 Mirror configuration. The USB Drive does not show.

I would appreciate any other steps to take to find out if anything is wrong with the USB2 driver.

---

### Post by rbmorse on 2019-08-20
There are a couple of settings in your BIOS setup that you should check.  They're sort of described on pages 45 and 46 of your owner's manual.  If you don't have one, you can see an on-line version at [https://www.manualslib.com/manual/549876/Gigabyte-Ga-970a-D3p.html?page=45#manual](https://www.manualslib.com/manual/549876/Gigabyte-Ga-970a-D3p.html?page=45#manual)

In particular, make sure the setting for "onboard USB device" is set to enabled (the default).  

Specifically in regard to Linux, I'm not sure which of the options for XCHi and EHCi handoff is recommended.  EHCi is the standard for USB 2.0, though, so you might just flip that setting, then press <f10> to save changes and exit setup.  That will reboot the machine.  See if it makes a difference.  If it doesn't, repeat the drill and put it back to the default setting.  

Same for the "legacy device support" setting.

Unrelated, but since you're in settings:  If you haven't replaced the battery on the motherboard in the last three years, now would be a good time to do so.

---

### Post by artist-wavenet on 2019-08-24
In my EUFI Firmware Settings has separate enables for Onboard USB, and Legacy USB are and were on. Testing with Legacy off did not make a difference.

I tested all four combination states of XCHI and EHCI being on and off. The USB2 ports did not work with any of them.

---

