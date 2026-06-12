---
title: "[SOLVED] USB Bluetooth adapter not Detected"
date: 2008-10-09
forum: Hardware
---

### Post by dethredic on 2008-10-09
I just purcahsed a cheap $4 USB Bluetooth adapter, so I can wireless transfer files to my phone, but when I booted into Ubuntu it did not detect it at all.
Is there anyway I can get it working in Ubuntu?

---

### Post by dethredic on 2008-10-10
anyone?

---

### Post by dethredic on 2008-10-11
someone?

---

### Post by getnripped on 2008-10-11
What brand? and where from?

---

### Post by getnripped on 2008-10-12
> **dethredic said:**
> I just purcahsed a cheap $4 USB Bluetooth adapter, so I can wireless transfer files to my phone, but when I booted into Ubuntu it did not detect it at all.
Is there anyway I can get it working in Ubuntu?

well I hope this helps you

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by dethredic on 2008-10-12
> **getnripped said:**
> What brand? and where from?

It is some no name brand.

---

### Post by getnripped on 2008-10-13
Hmm odd that there is no name on it. some one had to manufacture it. I am joking ;). Just try following all the steps on the link. If that does not help then you may want to return it and try newegg.com they have customer reviews that will tell you if they are functional with Ubuntu. Another option is to install all the Blue tooth apps and test if each one detects it. When / if one does uninstall all but that one.

---

### Post by dethredic on 2008-10-16
This is with the USB thing pluged in:
> phil@Ubuntu:~$ sudo lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 046d:c227 Logitech, Inc. 
Bus 001 Device 005: ID 046d:c226 Logitech, Inc. 
Bus 001 Device 004: ID 0c10:0000  
Bus 001 Device 003: ID 046d:c223 Logitech, Inc. 
Bus 001 Device 002: ID 046d:c049 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

This is without it pluged in:
> 
phil@Ubuntu:~$ sudo lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 046d:c227 Logitech, Inc. 
Bus 001 Device 005: ID 046d:c226 Logitech, Inc. 
Bus 001 Device 003: ID 046d:c223 Logitech, Inc. 
Bus 001 Device 002: ID 046d:c049 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

I am not sure if this means it sees it or not.

Also, I read some reviews on the site where I bought it from and people say it would by default in 8.04.

---

### Post by getnripped on 2008-10-17
sorry for my delay.. check out blueman bluetooth manager. just google it and DL from their site. it is a GUI Bluetooth manager. When installed run it via terminal "blueman" and there you go

---

### Post by dethredic on 2008-10-17
Ok, I ran it and got this:
> phil@Ubuntu:~$ blueman

(blueman:7120): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
* Initializing 'Bluetooth.manager' Class
Traceback (most recent call last):
  File "/usr/bin/blueman", line 130, in <module>
    Globals.Manager = manager()
  File "/usr/lib/python2.5/site-packages/blueman/Bluetooth/manager.py", line 40, in __init__
    self.obj = self.bus.get_object('org.bluez', '/org/bluez')
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.bluez was not provided by any .service files
phil@Ubuntu:~$ 


---

### Post by getnripped on 2008-10-18
What version did you DL and version of Ubuntu are you running?

---

### Post by dethredic on 2008-10-18
Ubuntu 8.04.

I followed these instructions:
[http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56](http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56)

---

### Post by era86 on 2008-10-22
Were you able to get this working?  I am currently shopping around for a USB Bluetooth adapter and I want to make sure the one I purchase works.  So, I figure I'd bump this thread a bit.

---

### Post by dethredic on 2008-10-22
Nope, but according to the reviews it works.

---

### Post by getnripped on 2008-10-23
Have you tried restarting your bluetooth? run this code in terminal them open Blueman ensure that your device is visbile and try it again. 
```
sudo /etc/init.d/bluetooth restart
```

---

### Post by dethredic on 2008-10-23
> **getnripped said:**
> Have you tried restarting your bluetooth? run this code in terminal them open Blueman ensure that your device is visbile and try it again. 
```
sudo /etc/init.d/bluetooth restart
```

Wow, thanks!!

This thing is now up and running!

---

### Post by getnripped on 2008-10-23
> **dethredic said:**
> 

This thing is now up and running!
No problem at all I am glad you got it working.

---

### Post by dethredic on 2008-10-25
> **getnripped said:**
> No problem at all I am glad you got it working.

Ok, one more thing. I have to restart the bluetooth service every time. I reboot my computer to be able to start blueman.

I tried adding blueman to my startup items, but it doesn't work cause I haven't restarted bluetooth.

So, can I fix this or somehow combine these two commands:

sudo /etc/init.d/bluetooth restart
blueman

---

### Post by getnripped on 2008-10-27
sorry I was not able to respond till now. I am sure there is away. let me look around my PC and look in to some other options.

---

### Post by shak541 on 2008-10-27
go into system then administration, then finally services and make sure bluetooth services are enabled.. also i own a kensington micro bluetooth adapter :D

---

### Post by dethredic on 2008-10-29
> **shak541 said:**
> go into system then administration, then finally services and make sure bluetooth services are enabled.. also i own a kensington micro bluetooth adapter :D

Thanks! This was the fix.

---

### Post by getnripped on 2008-10-30
another thing to check is your bluetooth pref. make sure you have it set to send/receive files. I had a problem getting that to work for a while. Then i changed settings and now it works fine.

---

