---
title: "USB DVB device (Hauppauge NOVA-T-USB 2)"
date: 2010-06-23
forum: Hardware
---

### Post by PendragonUK on 2010-06-23
Ubuntu thinks it's identified it and has installed drivers. It's not working... Not even a light on the front. Any and all help gratefully received.


[[img]http://j.imagehost.org/t/0968/Screenshot-Hardware_Drivers.jpg[/img]](http://j.imagehost.org/view/0968/Screenshot-Hardware_Drivers)

Ubuntu 10.04 64bit fully upto date.
Hauppauge NOVA-T-USB 2
93000 Rev B8A2 Lot 4905

[[img]http://a.imagehost.org/t/0093/Hauppauge-WinTV-Nova-T-USB-2.jpg[/img]](http://a.imagehost.org/view/0093/Hauppauge-WinTV-Nova-T-USB-2)

Hardware Report attached for full system spec.

---

### Post by IcarusR on 2010-06-24
Check to see if the firmware is being loaded by unplugging it, plugging back in & form terminal run

```
dmesg
```

You should see lines like this... if not check the firmware is in the correct place as per links below.

```
- usb 5-2: USB disconnect, address 3
- usb 5-2: new high speed USB device using ehci_hcd and address 8
- dvb-usb: found a 'Hanftek UMT-010 DVB-T USB2.0' in cold state, will try to load a firmware
- dvb-usb: downloading firmware from file 'dvb-usb-umt-010-02.fw' to the 'Cypress FX2'
- dvb-usb: Hanftek UMT-010 DVB-T USB2.0 successfully initialized and connected.
- usb 5-2: USB disconnect, address 8
- dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
```

What application are you testing with ?
I used Kaffeine when I tried a Nova T usb stick, worked well.

Info on installing here

[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_USB2]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_USB2")

& here 

[http://www.linuxtv.org/wiki/index.php/DVB_USB#Hauppauge_WinTV-NOVA-T_usb2]("http://www.linuxtv.org/wiki/index.php/DVB_USB#Hauppauge_WinTV-NOVA-T_usb2")

---

### Post by PendragonUK on 2010-06-24
Thank you for your reply, this is going to be a little embarrassing...

After a few hours, that involved a reboot or two it started working. The signal strength appears to be very week. That's odd because under windows it's just fine. So I fear there is something amiss.

---

### Post by dino99 on 2010-06-24
lshw (into a console) will give you the real chipset's name of this stick

---

