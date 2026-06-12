---
title: "sony ericsson md400 neewbe."
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by koffejensen on 2009-06-03
Hi plz help me install and config my sonyericcson md400 telenor 3g modem. I cant get it work PLz help.
MVH kristoffer

---

### Post by GeorgeVita on 2009-06-03
Hi **koffejensen**,
what is the exact version of Ubuntu? (9.04?)

Right click the Network Manager icon (at default is on top panel, left to the speaker sign), Edit Connections, Mobile Broadband. Click on any existing connection and delete it. Then shut down, boot without the modem, wait for the system to stabilise, attach the modem, wait 1 minute (maximum) for a wizard to start. If started, follow instructions to setup the connection. Left click network Manager icon and then the provider's name to connect.

If the wizard does not appear, open a terminal window (Applications > Accessories, Terminal) and try:

[B]dmesg
lsusb
ls /dev/ttyU* /dev/ttyA* /dev/ttyH*[/B]

Post here _the last 10-15 lines_ of dmesg (concerning /dev/tty... and usbserial or option driver).
Post the output of the other two commands.

The **dmesg** command will show all system activity after inserting the modem, **lsusb** will show all USB peripherals attached and their vendor/product IDs and **ls /dev/tty...** will list any configured serial communication ports.

Regards,
George

---

### Post by koffejensen on 2009-06-03
thanx i will try , and yes its 9.04 :p

---

### Post by JesperL on 2009-06-08
Hi,

I worked out a way to get my MD400 and bredbandsbolaget modem yesterday using the usb_modeswitch program that can be downloaded
[http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch)

The modem can be switched with the command given in
[http://ubuntuforums.org/showthread.php?p=7412527#post7412527](http://ubuntuforums.org/showthread.php?p=7412527#post7412527)

I have not tried to make this work automatically yet but it should be possible.
//Jesper

---

