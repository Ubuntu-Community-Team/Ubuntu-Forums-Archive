---
title: "USB keyboard/mouse/ports stop working after a while"
date: 2014-01-17
forum: Hardware
---

### Post by Yuzem on 2014-01-17
Hi, the problem started when I changed my motherboard. I am now using an ASUS M3N-HD/HDMI.
I hava a wireless keyboard + mouse combo (Logitech mk320), never had a problem with my previous motherboard.
Everything works perfectly at first, but after a while, the keyboard stops working, the mouse keeps working and the multimedia keys on the keyboard work but the rest of the keyboard does not.
Some times it is the mouse that stops working and not the keyboard.
If when either the mouse or the keyboard stop working I change to another USB port there is no change shown by lsusb and both the mouse and the keyboard stop working and actually all the USB ports stop working.
Restarting Xorg (sudo killall Xorg) does not solve the problem, I have to restart the system and everything works again... at least for a while.
I'm using Ubuntu 13.10
I don't know what to do, I tried changing options in the BIOS and in GRUB but with no luck.
Any advice is welcome.
Thanks in advance.

---

### Post by Rob Sayer on 2014-01-24
I'm having a similar problem with kubuntu 12.04.  So far I've just been searching ubuntuforums and askubuntu but I must the number of responses to others having problems with usb ports is terrible.

---

### Post by Yuzem on 2014-01-24
Hi Rob, I could not solve my problem so I went back to my previous motherboard. In my case it seems to be the same problem described in [this]("http://www.nvnews.net/vbulletin/showthread.php?t=123583") thread. I believe it is a hardware problem related to the integrated graphics, audio and usb IRQ assignment.
The best way I know you may be able to solve this problem (if it is the same problem I have) is to desactivate all onboard USB functions in the BIOS and buy a PCI card with USB ports.
Before doing that try using some boot flags as described in [this]("http://askubuntu.com/questions/69594/my-usb-ports-randomly-stop-working-till-a-reboot") thread.

---

