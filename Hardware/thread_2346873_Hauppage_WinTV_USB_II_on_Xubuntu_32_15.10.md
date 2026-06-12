---
title: "Hauppage WinTV USB II on Xubuntu 32 15.10"
date: 2016-12-19
forum: Hardware
---

### Post by oldhwuser on 2016-12-19
Hello, I would like to use an Hauppage WinTV-USB II PAL (made about year 2000, chipset em2820/em2840, card 4) on a Mac mini 32 bit made about 2004, on which I happily use Xubuntu 16.10 (4.8.0-30-generic), to made some analog video recording. I've installed some video editing software and test utilities: Qt V4L2 test utility says erroneously that it is an Hauppage WinTV USB Pro (similar name but different chipset) and doesn't do any preview; the same happens with Xubuntu control panel for video4linux. The other softwares say they can't open /dev/video0.

However lsusb seems to recognize it correcly:
```
Bus 001 Device 005: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 001 Device 003: ID 03f0:2504 Hewlett-Packard DeskJet F4200 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 05ac:8240 Apple, Inc. Built-in IR Receiver
Bus 005 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0573:4d21 Zoran Co. Personal Media Division (Nogatech) Hauppauge WinTV-USB II (PAL)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1241:0504 Belkin Wireless Trackball Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
Of course I googled a lot and it seems to me that this hw can function on Linux and that the trouble is in the module used by video4linux: it is usbvision but IMO it should be em28xx. I've tried to insmod em28xx putting it in /etc/modules but systemd complains and doesn't load it at startup.
What can I do ? Perhaps installing an old version of video4linux could solve but I'm not sure and besides I don't know how to do this and where to find the old version.
Can anyone help me or give me more information ?
Thanks a lot.

---

### Post by mörgæs on 2016-12-20
Hi, welcome to the fora.

Just to rule out misunderstandings: Since you mention kernel 4.8.0-30 I assume it is about Xubuntu 16.10, not 15.10 right?

---

### Post by oldhwuser on 2016-12-20
Yes indeed, Xubuntu 16.10, I immediately correct. I'm getting old... Excuse me.

---

