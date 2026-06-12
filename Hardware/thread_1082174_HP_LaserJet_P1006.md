---
title: "HP LaserJet P1006"
date: 2009-02-27
forum: Hardware
---

### Post by Guns90 on 2009-02-27
Good Afternoon.  I just bought an HP LaserJet P1006 printer to try and do some economical printing.  The installation CD doesn't work and I'm not having any luck trying to get 8.10 to recognize this printer.  I went to HPLIPopensource and downloaded the HPLIP-3.9.2.run, but I can't get it to open and install.  Can I get a little help please?

---

### Post by taurus on 2009-02-27
Have you looked in System -> Administration -> Printing -> New to configure it?  Is it a UBS or a parallel printer?

---

### Post by Guns90 on 2009-02-27
Yes Taurus, it shows up in the Printer Configuration window.  Everything looks like I believe it  is supposed to; however, I can't get the printer to react to any print commands, even the 'Print Test Page'.

---

### Post by taurus on 2009-02-27
Any error message when you try to do the Print Test Page or it just sits there?

I assume it is a USB printer and it's on.

---

### Post by Guns90 on 2009-02-27
No, I don't get any error msg. It just sits there.  Yes it is a USB printer,  yes its turned on, and I have disconnected and reconnected both ends of the usb cable.

---

### Post by Guns90 on 2009-02-27
Thanks for your help, Taurus.  I'm not really sure what exactly I changed to fix it, but its working now.  I kept changing the settings on the the server settings.  Some combination worked.  Thanks again.

---

### Post by fatiberio on 2009-04-22
I have installed in my system the ubuntu packages hplip and hpijs.
I set up the printer and it correctly identified the printer 
hp-P1006. But when I print via USB (evince) or even lpr , nothing seems 
to happen.

Am I using the wrong command to print? 
I have also downloaded hplip-3.9.2.. but then it asks me for basics that I need 
to install things that for sure are already there and upgraded like "gcc'.

Thank you
fatiberio

Here are the syslog messages..

Apr 21 00:17:09 rayonvert hal_lpadmin: Found configured printer: HP_LaserJet_P1006
Apr 21 00:17:09 rayonvert NetworkManager: <debug> [1240287429.747332] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3e17_AC2070X_if0_printer_noserial'). 
Apr 21 00:17:10 rayonvert foo2xqx-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
Apr 21 00:17:10 rayonvert foo2xqx-wrapper: foo2xqx -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7  -u 177x84 -l 177x84       
Apr 21 00:17:31 rayonvert HP_LaserJet_P1006?serial=AC2070X: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Apr 21 00:19:05 rayonvert HP_LaserJet_P1006?serial=AC2070X: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Apr 21 00:19:05 rayonvert kernel: [14523.756490] audit(1240287545.355:6): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=21511 profile="/usr/sbin/cupsd" namespace="default"
Apr 21 00:19:05 rayonvert foo2xqx-wrapper: foo2xqx-wrapper -r1200x600 -p1 -s7 -m1 -d1 -n1
Apr 21 00:19:06 rayonvert foo2xqx-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
Apr 21 00:19:06 rayonvert foo2xqx-wrapper: foo2xqx -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7  -u 177x84 -l 177x84       
Apr 21 00:19:27 rayonvert HP_LaserJet_P1006?serial=AC2070X: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused

---

### Post by jfrorie on 2009-05-26
I don't know if you are still subscribed, but go here for the solution.

I just installed one last and it works pretty well.

[http://foo2xqx.rkkda.com/](http://foo2xqx.rkkda.com/)


> **fatiberio said:**
> I have installed in my system the ubuntu packages hplip and hpijs.
I set up the printer and it correctly identified the printer 
hp-P1006. But when I print via USB (evince) or even lpr , nothing seems 
to happen.

Am I using the wrong command to print? 
I have also downloaded hplip-3.9.2.. but then it asks me for basics that I need 
to install things that for sure are already there and upgraded like "gcc'.

Thank you
fatiberio

Here are the syslog messages..

Apr 21 00:17:09 rayonvert hal_lpadmin: Found configured printer: HP_LaserJet_P1006
Apr 21 00:17:09 rayonvert NetworkManager: <debug> [1240287429.747332] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_3e17_AC2070X_if0_printer_noserial'). 
Apr 21 00:17:10 rayonvert foo2xqx-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
Apr 21 00:17:10 rayonvert foo2xqx-wrapper: foo2xqx -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7  -u 177x84 -l 177x84       
Apr 21 00:17:31 rayonvert HP_LaserJet_P1006?serial=AC2070X: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Apr 21 00:19:05 rayonvert HP_LaserJet_P1006?serial=AC2070X: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Apr 21 00:19:05 rayonvert kernel: [14523.756490] audit(1240287545.355:6): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=21511 profile="/usr/sbin/cupsd" namespace="default"
Apr 21 00:19:05 rayonvert foo2xqx-wrapper: foo2xqx-wrapper -r1200x600 -p1 -s7 -m1 -d1 -n1
Apr 21 00:19:06 rayonvert foo2xqx-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN  
Apr 21 00:19:06 rayonvert foo2xqx-wrapper: foo2xqx -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7  -u 177x84 -l 177x84       
Apr 21 00:19:27 rayonvert HP_LaserJet_P1006?serial=AC2070X: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused

---

