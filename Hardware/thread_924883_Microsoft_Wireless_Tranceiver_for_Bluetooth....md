---
title: "Microsoft Wireless Tranceiver for Bluetooth..."
date: 2008-09-20
forum: Hardware
---

### Post by bhart007 on 2008-09-20
Has anyone had any luck getting this USB BT adapter to work?  LSPCI does not show it and I have bluetooth, bluez-audio, bluez-utils, bluez-gnome and gnome bluetooth installed.

Thanks!

---

### Post by bhart007 on 2008-09-21
bump

---

### Post by bhart007 on 2008-09-22
A slight update here.. I just discovered the hci commands, and not on these forums for some damned reason.

Anyway I can run an hcitool scan right after hitting the connect button on both a Dell BT Keyboard and the corresponding mouse.  the scan picks up the keyboard however an actual connection is not established.

---

### Post by bhart007 on 2008-09-22
Also hcitool dev returns:  hci0   00:50:f2:e4:61:dd

So it sees something.. IDK what the hell that device is.

---

### Post by IntuitiveNipple on 2008-09-22
If it's a USB device you'll not see it with lspci, you need:
```

lsusb

```

---

### Post by bhart007 on 2008-09-22
Ok cool, :

allanon@sputnik:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 045e:007e Microsoft Corp. Wireless Transceiver for Bluetooth
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 413c:3016 Dell Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 050d:0815 Belkin Components 
Bus 001 Device 001: ID 0000:0000  
allanon@sputnik:~$ 


So my box sees it.. but gnome bluetooth doesnt see it.  I've tried restarting the bluetooth service, but when I hit the connect button on the keyb or mouse nothing happens.  I can't find (if one exists) a scan or connect command in the BT gui.

I tried editting the hcid.conf file and setting security to none, and commenting out the default passkey line.  Still no dice.

---

### Post by IntuitiveNipple on 2008-09-23
Well, hcitool has confirmed the device is known by the Bluetooth daemons.

What precisely does the Bluetooth Applet show. Is it visible in the notification area? If you right-click it, choose "Preferences", what is the title of the first tab, and is it the same as the "Adapter Name" field? They should both be the name of the PC.

Is it set to "Visible and connectable for other devices" ?

I guess you'll want the keyboard and mouse connected as soon as the Bluetooth services start, not wait for the user to log-in.

In that case they'll need to add them to the system configuration. Here's a guide "[Howto Setup Bluetooth Keyboard and Mouse in Ubuntu](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)".

---

### Post by bhart007 on 2008-09-23
Actually no, the applet does not appear in the system tray.  I've manually ran it from Prefs->Bluetooth  and it is set to visible.  The first tab is the name of the pc appended with a "-0", same as with the adapter name too.

I will follow your link.  thanks

---

