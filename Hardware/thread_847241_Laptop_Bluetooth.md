---
title: "Laptop Bluetooth"
date: 2008-07-02
forum: Hardware
---

### Post by zyat01 on 2008-07-02
Dear all,

I'd be thankful if I could get help with the following issue:

I use a USB bluetooth dongle on a Sony VGN-NR260E and had some incomplete bluetooth functionality until I upgraded to 8.04 Hardy Heron Kubuntu KDE 4.0;

Now it is impossible to use KDE3 bluetooth applications e. g. OBEX transfer etc.or connect a mouse;

dmesg | grep Bluetooth

[   55.176706] Bluetooth: Core ver 2.11
[   55.177268] Bluetooth: HCI device and connection manager initialized
[   55.177273] Bluetooth: HCI socket layer initialized
[   55.275001] Bluetooth: L2CAP ver 2.9
[   55.275007] Bluetooth: L2CAP socket layer initialized
[   55.811914] Bluetooth: RFCOMM socket layer initialized
[   55.811934] Bluetooth: RFCOMM TTY layer initialized
[   55.811936] Bluetooth: RFCOMM ver 1.8
[ 1037.479385] Bluetooth: HCI USB driver ver 2.9


hcitool dev

Devices:
	hci0	00:19:15:5F:5F:22

hcitool scan

Scanning ...
	00:12:5A:69:C7:88	Microsoft Bluetooth Notebook Mouse 5000
	00:1E:7D:94:3D:0F	SGH-i61

SGH-i61 being the phone

hcitool cc

to any of the above addresses then doesn't result in a connection;

i cannot start kbluemon or any similar kde3 program;

i would be thankful for suggestions on how to solve this problem;

thanks

---

### Post by AlesUbu123 on 2008-07-04
Have you tried Blueman for connecting bluetooth devices?
[http://blueman.tuxfamily.org/]("http://blueman.tuxfamily.org/")

BR

---

