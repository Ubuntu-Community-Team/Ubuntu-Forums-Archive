---
title: "WinTouch Touch Screen Kit"
date: 2011-02-24
forum: Hardware
---

### Post by GeoMX on 2011-02-24
[SIZE="2"]I've just got a WinTouch touch screen kit:
[http://www.amazon.com/WinTouch-Converts-Monitor-Installation-Required/dp/B00374ON22](http://www.amazon.com/WinTouch-Converts-Monitor-Installation-Required/dp/B00374ON22)

I'm trying to find out whether it is supported under Linux, I've just sent an email to manufacturer but would like to know of experiences from people here :).

In Windows, this panel reports as a "HID Touch Panel". It has a 4096x4096 touch resolution (it includes a CD with a calibration program).

In my Ubuntu 10.04 installation, when I touch on it, it sends clicks but cursor does not move from top left corner, so everytime I touch the panel I open/close Gnome Applications Menu.

lsusb:
[FONT="Courier New"]Bus 003 Device 003: ID 10c4:0001 Cygnal Integrated Products, Inc.[/FONT]

cat /proc/bus/input/devices:
[FONT="Courier New"]I: Bus=0003 Vendor=10c4 Product=0001 Version=0101
N: Name="HID TOUCH HID Touch Panel"
P: Phys=usb-0000:00:12.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse2 event5 
B: EV=1b
B: KEY=c01 0 70000 0 0 0 0 0 0 0 0
B: ABS=f
B: MSC=10
[/FONT]
Please tell me of any other info you may need and thanks in advance for any help :).[/SIZE]

---

