---
title: "Logitech Unifying Receiver stops working after logging in (M325)"
date: 2022-04-24
forum: Hardware
---

### Post by vw16v on 2022-04-24
Hello, I recently was messing around and trying to disable the touch screen on my Ubuntu 20.04 load for the "Wayland" Session GUI. My screen is cracked so it causes it to freak out.

I currently have GMONE on Xorg, Ubuntu, Xfce, GNOME (wayland) and Ubuntu on Wayland (Wayland) sessions.
I probably should of left it alone since I was able to disable the touch screen without issues on Ubuntu & Xfce. The Wayland is much more difficult and cumbersome to disable the touchscreen on.

Anyways, after I was doing various things to try and disable the touchscreen on Wayland session it seems to have broken the Logitech USB receiver for my mouse when I logon to my session. Upon booting up and before logging into any of the above sessions the mouse works without issues. However, right after I login to any of the sessions it immeditely stops working and I have to remove the mouse receiver and plug it back in. Then it works fine. I even tried a different USB port and a different mouse m325 mouse I have and have the same issues.

I noticed this in blacklist.conf but I believe this is default. I tried commenting out these two lines and rebooting but that did not help.

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

Any ideas why I have to disconnect the receiver and plug it back in AFTER logging in to any of my various sessions? Seems pretty strange but some command I ran when trying to disable my touchscreen appears to have caused this problem. I was also wondering if I could simulate removing and plugging in the USB receiver through a rc.local file or some automated way?

If the computer goes to sleep the mouse still works fine. It's only if I log out of the session or restart. The mouse works on the logon screen but as soon as I logon to any session it stops working until I remove and re-insert the USB receiver. Appreciate any input or ideas. 

Here's some various output showing the hardware address of the receiver, etc.

```
asus:/etc/udev/rules.d$ sudo lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 03eb:8417 Atmel Corp. 
Bus 001 Device 004: ID 13d3:5188 IMC Networks 
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0b95:1790 ASIX Electronics Corp. AX88179 Gigabit Ethernet
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 012: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


asus:~$ dmesg |grep Receiver
[ 1347.539451] usb 3-3: Product: USB Receiver
[ 1347.547796] logitech-djreceiver 0003:046D:C52B.001D: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-3/input2
[ 1381.770535] usb 3-3: Product: USB Receiver
[ 1381.779788] logitech-djreceiver 0003:046D:C52B.0021: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-3/input2
[ 1416.050282] usb 3-3: Product: USB Receiver
[ 1416.059624] logitech-djreceiver 0003:046D:C52B.0025: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-3/input2
[15692.122111] usb 3-3: Product: USB Receiver
[15692.130523] logitech-djreceiver 0003:046D:C52B.0029: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-3/input2

asus:~$ grep . /sys/bus/usb/devices/*/product
/sys/bus/usb/devices/1-1.2/product:USB2.0 UVC HD Webcam
/sys/bus/usb/devices/1-1.3/product:Atmel maXTouch Digitizer
/sys/bus/usb/devices/3-3/product:USB Receiver
/sys/bus/usb/devices/4-2/product:AX88179
/sys/bus/usb/devices/usb1/product:EHCI Host Controller
/sys/bus/usb/devices/usb2/product:EHCI Host Controller
/sys/bus/usb/devices/usb3/product:xHCI Host Controller
/sys/bus/usb/devices/usb4/product:xHCI Host Controller

```

---

