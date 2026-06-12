---
title: "LIRC / Infrared / IVTV issues"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by CA_Warren on 2007-04-04
Ubuntu 6.10, fully updated
Dell Dimension 4700

Hauppauge WinTV 150 capture card w/black and gray remote


Trying to install MythTV, but I'm having some issues. I was following [this]("http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft") tutorial on setting up the remote, and at first everything worked. I then restarted (as instructed), and irw no longer reports any readings from the remote. IVTV module is installed, as is the lirc_i2c module. Attempts to remove/re-insert them with rmmod/modprobe results in Linux telling me they're in use. 

[FONT="Courier New"]dmesg | tail [/FONT] now looks like:

[FONT="Courier New"][17179604.116000] apm: disabled - APM is not SMP safe.
[17179609.796000] Bluetooth: Core ver 2.8
[17179609.796000] NET: Registered protocol family 31
[17179609.796000] Bluetooth: HCI device and connection manager initialized
[17179609.796000] Bluetooth: HCI socket layer initialized
[17179609.820000] Bluetooth: L2CAP ver 2.8
[17179609.820000] Bluetooth: L2CAP socket layer initialized
[17179609.820000] Bluetooth: RFCOMM socket layer initialized
[17179609.820000] Bluetooth: RFCOMM TTY layer initialized
[17179609.820000] Bluetooth: RFCOMM ver 1.7[/FONT]

[FONT="Courier New"]ps ax | grep lirc[/FONT] outputs:

[FONT="Courier New"]3214 ?        S      0:00 [lirc_dev]
 4204 ?        Ss     0:00 /usr/sbin/lircd --device=/dev/lirc0
 4206 ?        Ss     0:00 /usr/sbin/lircmd
 4327 ?        Ss     0:00 /usr/sbin/inputlircd /dev/input/event0 /dev/input/event1 /dev/input/event2
13453 pts/0    S+     0:00 grep lirc[/FONT]

[FONT="Courier New"]sudo mode2 -d /dev/lirc0[/FONT] outputs:

[FONT="Courier New"][/FONT]mode2: error opening /dev/lirc0
mode2: Device or resource busy

Any ideas as to what the problem is would be greatly appreciated - thanks a lot!

If you need any other details, just say so.<br /><br />
----------------------------------------<br />

----------------------------------------<br /><br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by majoridiot on 2007-04-07
i recommend installing from this guide: [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

which works very well with both the pvr-150's usb or on-card ir receiver/blaster.

---

