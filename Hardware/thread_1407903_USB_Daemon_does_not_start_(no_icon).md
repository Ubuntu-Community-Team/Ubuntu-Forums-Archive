---
title: "USB Daemon does not start (no icon)"
date: 2010-02-15
forum: Hardware
---

### Post by le_vainqueur on 2010-02-15
I running Ubuntu 9.10 on my desktop and have plugged a bluetooth USB dongle in so that I can connect my Logitech PS3 keyboard.  Unfortunately, I'm have no experience with this.  I have tried to find solutions from searching this forum and others, but haven't had any success yet.


When I try to start the daemon, however, there is no effect.  According to this web site

> [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

I tried the following command

> sudo /etc/init.d/bluetooth start

However, nothing happened. I was expecting to see a bluetooth icon in the system tray that I could use to set up my devices.  If I look in the system manager, "bluetooth-aplett" is in the list of running processes.  I'm not sure if this is related or not, but thought it was worth pointing out.

Since it should, theoretically, be running, I tried **hcitool dev** while holding the detect button on the keyboard, but the output was as follows.

> Devices:

When I try **lsusb** I get the following in the output, so I know the device is being recognized properly.

> Bus 002 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter

I'm not sure where my problem is.  I read that the Logitech PS3 keyboard would work in Ubuntu, so I'm guessing the problem is either with my dongle or with the getting the daemon up and running.  Since I can't even get the bluetooth icon to start up, I don't have a way to test my dongle.  

Any suggestions/guidance would be appreciated.


Thanks,

LV

---

### Post by le_vainqueur on 2010-02-16
*bump*

---

### Post by le_vainqueur on 2010-02-17
*bump*

I'd really apreciate any help you could offer.

---

### Post by le_vainqueur on 2010-02-20
Pleas, help

---

### Post by le_vainqueur on 2010-02-21
Still trying stuff.  Here's a little update.

If I go to System > Preferences > Bluetooth, it says there are no Bluetooth adaptersconnected, even though it shows up when I use the lsusb command.

I went into the running processes and killed the bluetooth-applet to see if I could start it manually.  When trying to restart it, I got the following output.

> :~$ bluetooth-applet
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

Not sure what it means, but it doesn't look good. The Bluetooth applet still doesn't show up in the taskbar.  In the Bluetooth Preferences dialogue, I do have the "show bluetooth icon" option enabled.

---

