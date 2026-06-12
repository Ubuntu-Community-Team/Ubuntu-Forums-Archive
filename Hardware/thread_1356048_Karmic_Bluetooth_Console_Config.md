---
title: "Karmic Bluetooth Console Config"
date: 2009-12-15
forum: Hardware
---

### Post by pashdown on 2009-12-15
This documentation - [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) explains how to setup Bluetooth devices via the console on Ubuntu.  Unfortunately, Karmic has no /etc/default/bluetooth file, nor does it appear one is referenced anywhere.  I can not find any documentation as to how to configure a Bluetooth keyboard & mouse permanently via the console.  This is a lightweight system, so I don't want to install Gnome.

I've searched, downloaded the source, and looked at [http://bluez.org]("http://bluez.org/") all to no avail.  Can someone give me some pointers please?

---

### Post by keithspg on 2010-03-17
Yes, please. There is a bug in the gnome applet which will not allow me to use a pre set pin for my BT serial (times out and tries to use a 6 digit random pin instead) I am fine with setting uo a persistent BT serial connection from the command line, but am not sure how to do it. If I try # hcitool scan, the BT serial connection does not show up. 

Any help appreciated.

Keith

---

### Post by TutTheMummy on 2010-05-01
I use XBMC Live as a Media Center connected to my TV. I bought a bluetooth keyboard to use as a remote.
XBMC Live is a modified UI running on top of Ubuntu Karmic. Because of this, I have been unable to permanently pair my keyboard since I can't use the gnome bluetooth applet, because it doesn't have the gnome interface!

I have been able to use hidd to connect my keyboard, but I have to reconnect it each time I want to use it since it sleeps after 10 minutes.

I would also like to know how can I configure the pairing using the console? What are the config files for pairing?

---

