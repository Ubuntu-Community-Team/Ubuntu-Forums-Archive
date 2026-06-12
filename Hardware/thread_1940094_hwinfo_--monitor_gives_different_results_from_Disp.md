---
title: "hwinfo --monitor gives different results from Displays."
date: 2012-03-13
forum: Hardware
---

### Post by jiapei100 on 2012-03-13
Hi, all:

Environment:
OS: Ubuntu 11.10 oneiric
Video Card: AMD Radeon HD 6870
Monitor: Asus 23.6'' 

What I observed may only tell a truth that
"monitor is different from displays".

1) This is what I obtained by typing
> hwinfo --monitor from bash
> 
hwinfo --monitor
> hal.1: read hal dataprocess 9851: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
42: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 1400x1050@77Hz
  Driver Info #0:
    Max. Resolution: 1400x1050
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-85 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown


2) However, if I use the GUI application "Displays",
the resolution is clearly full HD, say: 1920*1080.

Can anybody help to explain it? 
BTW, how can I check the details of my monitor? I only know it's Asus 23.6'', but if I want to know the serial number and even more info about it, what can I do from within Ubuntu?

Thank you very much.

Best Regards
Pei

---

