---
title: "HP printer stopped printing..."
date: 2015-09-19
forum: Hardware
---

### Post by ric_Poirier on 2015-09-19
Hello everyone,

I have been printing with my printer for several months now on my Xubuntu machine and everything worked perfectly. Today, I was printing some documents when the printer suddenly stopped working. Here is some additional info:

**Printer:** HP LaserJet P1102W
**Connexion:** USB
**What IS working:** 
[LIST]
[*]the printer powers up; 
[*]I can manually print a test page when I press a certain button combination on the printer; 
[*]Xubuntu recognizes the printer (for example, it knows if it is connected or not). 
[/LIST]
What I have tried:
[LIST]
[*]rebooting the computer; 
[*]rebooting the printer; 
[*]disconnecting/reconnecting the USB cable on both ends; 
[*]unistalling and reinstalling the printer; 
[*]uninstalling and reinstalling HPLIP. 
[/LIST]

Unfortunately, nothing helps...

I have looked at the CUPs page ([http://localhost:631/printers/](http://localhost:631/printers/)) and the printer appears. Its status is: **Idle - "Sending data to printer."** Finally, I have followed [this page]("https://wiki.ubuntu.com/DebuggingPrintingProblems") (under USB printer) but I am not familiar with the output I see. I don't really know what to expect here... Here is the output:

```

lsmod | grep usb

usblp                  22901  0 
usb_storage            66545  2 uas
btusb                  32497  0 
bluetooth             446409  22 bnep,btusb,rfcomm
usbhid                 52616  0 
hid                   110426  2 hid_generic,usbhid

```

After unplugging:

```

tail -f /var/log/syslog

Sep 19 16:01:59 Hesse kernel: [ 4482.466014] usb 3-2: USB disconnect, device number 21
Sep 19 16:01:59 Hesse kernel: [ 4482.466376] usblp0: removed
Sep 19 16:01:59 Hesse udev-configure-printer: remove /devices/pci0000:00/0000:00:14.0/usb3/3-2
Sep 19 16:01:59 Hesse udev-configure-printer: URI of detected printer: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK1HV44PR1a, normalized: laserjet professional p1102w serial 000000000rk1hv44pr1a
Sep 19 16:01:59 Hesse udev-configure-printer: URI of print queue: usb://HP/LaserJet%20Professional%20P1102w?serial=000000000RK1HV44SI1c, normalized: laserjet professional p1102w serial 000000000rk1hv44si1c
Sep 19 16:01:59 Hesse udev-configure-printer: URI of detected printer: usb://HP/LaserJet%20Professional%20P1102w?serial=000000000RK1HV44PR1a, normalized: laserjet professional p1102w serial 000000000rk1hv44pr1a
Sep 19 16:01:59 Hesse udev-configure-printer: URI of print queue: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK1HV44PR1a, normalized: laserjet professional p1102w serial 000000000rk1hv44pr1a
Sep 19 16:01:59 Hesse udev-configure-printer: Queue ipp://localhost:631/printers/HP-LaserJet-Professional-P1102w has matching device URI
Sep 19 16:01:59 Hesse udev-configure-printer: Disabled printer ipp://localhost:631/printers/HP-LaserJet-Professional-P1102w as the corresponding device was unplugged or turned off
Sep 19 16:01:59 Hesse colord: device removed: sysfs-Hewlett-Packard-HP_LaserJet_Professional_P1102w

```

After plugging back:

```

Sep 19 16:03:39 Hesse kernel: [ 4582.283476] usb 3-2: new high-speed USB device number 22 using xhci_hcd
Sep 19 16:03:39 Hesse kernel: [ 4582.412348] usb 3-2: New USB device found, idVendor=03f0, idProduct=032a
Sep 19 16:03:39 Hesse kernel: [ 4582.412356] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep 19 16:03:39 Hesse kernel: [ 4582.412360] usb 3-2: Product: HP LaserJet Professional P1102w
Sep 19 16:03:39 Hesse kernel: [ 4582.412363] usb 3-2: Manufacturer: Hewlett-Packard
Sep 19 16:03:39 Hesse kernel: [ 4582.412367] usb 3-2: SerialNumber: 000000000RK1HV44PR1a
Sep 19 16:03:39 Hesse kernel: [ 4582.414944] usblp 3-2:1.0: usblp0: USB Bidirectional printer dev 22 if 0 alt 0 proto 2 vid 0x03F0 pid 0x032A
Sep 19 16:03:39 Hesse logger: loading HP Device 003 022
Sep 19 16:03:39 Hesse udev-configure-printer: add /devices/pci0000:00/0000:00:14.0/usb3/3-2
Sep 19 16:03:39 Hesse udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:14.0/usb3/3-2
Sep 19 16:03:39 Hesse udev-configure-printer: MFG:Hewlett-Packard MDL:HP LaserJet Professional P1102w SERN:- serial:000000000RK1HV44PR1a
Sep 19 16:03:40 Hesse kernel: [ 4583.447443] usblp0: removed
Sep 19 16:03:40 Hesse kernel: [ 4583.450903] usblp 3-2:1.0: usblp0: USB Bidirectional printer dev 22 if 0 alt 0 proto 2 vid 0x03F0 pid 0x032A
Sep 19 16:03:40 Hesse udev-configure-printer: URI contains USB serial number
Sep 19 16:03:40 Hesse udev-configure-printer: URI match: usb://HP/LaserJet%20Professional%20P1102w?serial=000000000RK1HV44PR1a
Sep 19 16:03:40 Hesse udev-configure-printer: SERN field matches USB serial number
Sep 19 16:03:40 Hesse udev-configure-printer: URI match: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK1HV44PR1a
Sep 19 16:03:40 Hesse udev-configure-printer: URI of detected printer: usb://HP/LaserJet%20Professional%20P1102w?serial=000000000RK1HV44PR1a, normalized: laserjet professional p1102w serial 000000000rk1hv44pr1a
Sep 19 16:03:40 Hesse udev-configure-printer: URI of print queue: usb://HP/LaserJet%20Professional%20P1102w?serial=000000000RK1HV44SI1c, normalized: laserjet professional p1102w serial 000000000rk1hv44si1c
Sep 19 16:03:40 Hesse udev-configure-printer: URI of detected printer: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK1HV44PR1a, normalized: laserjet professional p1102w serial 000000000rk1hv44pr1a
Sep 19 16:03:40 Hesse udev-configure-printer: URI of print queue: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK1HV44PR1a, normalized: laserjet professional p1102w serial 000000000rk1hv44pr1a
Sep 19 16:03:40 Hesse udev-configure-printer: Queue ipp://localhost:631/printers/HP-LaserJet-Professional-P1102w has matching device URI
Sep 19 16:03:40 Hesse udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/HP-LaserJet-Professional-P1102w
Sep 19 16:03:40 Hesse colord: Device added: sysfs-Hewlett-Packard-HP_LaserJet_Professional_P1102w

```

Then:

```

lsusb

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 059f:1057 LaCie, Ltd 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 5986:055c Acer, Inc 
Bus 003 Device 004: ID 8087:07dc Intel Corp. 
Bus 003 Device 010: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 003 Device 018: ID 17f6:0822 Unicomp, Inc 
Bus 003 Device 022: ID 03f0:032a Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And:

```

ls -l /dev/usb/lp* /dev/bus/usb/*/*

crw-rw-r--  1 root root 189,   0 Sep 19 14:47 /dev/bus/usb/001/001
crw-rw-r--  1 root root 189,   1 Sep 19 14:47 /dev/bus/usb/001/002
crw-rw-r--  1 root root 189, 128 Sep 19 14:47 /dev/bus/usb/002/001
crw-rw-r--  1 root root 189, 129 Sep 19 14:47 /dev/bus/usb/002/002
crw-rw-r--  1 root root 189, 256 Sep 19 14:47 /dev/bus/usb/003/001
crw-rw-r--  1 root root 189, 259 Sep 19 14:47 /dev/bus/usb/003/004
crw-rw-r--  1 root root 189, 260 Sep 19 14:47 /dev/bus/usb/003/005
crw-rw-r--  1 root root 189, 265 Sep 19 15:16 /dev/bus/usb/003/010
crw-rw-r--  1 root root 189, 273 Sep 19 15:57 /dev/bus/usb/003/018
crw-rw-r--+ 1 root lp   189, 277 Sep 19 16:03 /dev/bus/usb/003/022
crw-rw-r--  1 root root 189, 384 Sep 19 14:47 /dev/bus/usb/004/001
crw-rw-r--  1 root root 189, 385 Sep 19 14:47 /dev/bus/usb/004/002
crw-rw----  1 root lp   180,   0 Sep 19 16:03 /dev/usb/lp0

```

Then:

```

sudo usb_printerid /dev/usb/lp0

MFG:Hewlett-Packard;MDL:HP LaserJet Professional P1102w;CMD:ZJS,PJL,ACL,HTTP;CLS:PRINTER;DES:HP LaserJet Professional P1102w;FWVER:20101011;


sudo usb_printerid /dev/usb/lp1

Error: No such file or directory: can't open '/dev/usb/lp1'


hp-info -i

HP Linux Imaging and Printing System (ver. 3.14.3)
Device Information Utility ver. 5.2

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Using device: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK1HV44PR1a


HP Linux Imaging and Printing System (ver. 3.14.3)
System Tray Status Service ver. 2.0

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:127: RuntimeWarning: PyOS_InputHook is not available for interactive use of PyGTK
  set_interactive(1)

hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK1HV44PR1a

Device Parameters (dynamic data):
  Parameter                     Value(s)                                                  
  ----------------------------  ----------------------------------------------------------
  agent1-ack                    False                                                     
  agent1-desc                   Black toner cartridge                                     
  agent1-dvc                    0                                                         
  agent1-health                 0                                                         
  agent1-health-desc            Good/OK                                                   
  agent1-hp-ink                 False                                                     
  agent1-id                     0                                                         
  agent1-kind                   4                                                         
  agent1-known                  False                                                     
  agent1-level                  100                                                       
  agent1-level-trigger          0                                                         
  agent1-sku                    85A                                                       
  agent1-type                   1                                                         
  agent1-virgin                 False                                                     
  back-end                      hp                                                        
  cups-printers                 ['HP-LaserJet-Professional-P1102w']                       
  cups-uri                      hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK
                                1HV44PR1a                                                 
  dev-file                                                                                
  device-state                  1                                                         
  device-uri                    hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK
                                1HV44PR1a                                                 
  deviceid                      MFG:Hewlett-Packard;MDL: LaserJet Professional            
                                P1102w;CMD:ZJS,S,PJL,ACL,HT;CLS:PRINTER;D;D:H:HP LaserJet 
                                Pfefessional P110;F;FWVER:20101011;                       
  duplexer                      0                                                         
  error-state                   0                                                         
  host                                                                                    
  in-tray1                      1                                                         
  in-tray2                      1                                                         
  is-hp                         True                                                      
  media-path                    1                                                         
  panel                         0                                                         
  panel-line1                                                                             
  panel-line2                                                                             
  photo-tray                    0                                                         
  port                          1                                                         
  r                             0                                                         
  revision                      254                                                       
  rg                            000                                                       
  rr                            000000                                                    
  rs                            000000000                                                 
  serial                        000000000RK1HV44PR1a                                      
  status-code                   1000                                                      
  status-desc                   Idle                                                      
  supply-door                   1                                                         
  top-door                      1                                                         

Model Parameters (static data):
  Parameter                     Value(s)                                                  
  ----------------------------  ----------------------------------------------------------
  align-type                    0                                                         
  clean-type                    0                                                         
  color-cal-type                0                                                         
  copy-type                     0                                                         
  embedded-server-type          0                                                         
  fax-type                      0                                                         
  fw-download                   False                                                     
  icon                          HP_LaserJet_1012.png                                      
  io-mfp-mode                   6                                                         
  io-mode                       1                                                         
  io-support                    10                                                        
  job-storage                   0                                                         
  linefeed-cal-type             0                                                         
  model                         HP_LaserJet_Professional_P1102w                           
  model-ui                      HP LaserJet Professional p1102w                           
  model1                        HP LaserJet Professional P1102w Printer                   
  monitor-type                  0                                                         
  panel-check-type              0                                                         
  pcard-type                    0                                                         
  plugin                        1                                                         
  plugin-reason                 1                                                         
  power-settings                0                                                         
  pq-diag-type                  0                                                         
  r-type                        0                                                         
  r0-agent1-kind                4                                                         
  r0-agent1-sku                 85A                                                       
  r0-agent1-type                1                                                         
  scan-src                      0                                                         
  scan-type                     0                                                         
  status-battery-check          0                                                         
  status-dynamic-counters       0                                                         
  status-type                   8                                                         
  support-released              True                                                      
  support-subtype               2202411                                                   
  support-type                  2                                                         
  support-ver                   3.10.4                                                    
  tech-class                    ['LJZjsMono']                                             
  tech-subclass                 ['NoAutoDuplex']                                          
  tech-type                     3                                                         
  usb-pid                       810                                                       
  usb-vid                       1008                                                      
  wifi-config                   3                                                         

Status History (most recent first):
  Date/Time             Code   Status Description                        User      Job ID  
  --------------------  -----  ----------------------------------------  --------  --------
  09/19/15 16:10:34     1000   Idle                                      eric      0       

Done.

```

And:

```

hp-makeuri 003:022

HP Linux Imaging and Printing System (ver. 3.14.3)
Device URI Creation Utility ver. 5.0

Copyright (c) 2001-13 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

CUPS URI: hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK1HV44PR1a

Done.

```

And finally:
```

lpinfo -v

network lpd
network ipp14
network socket
direct hp:/usb/HP_LaserJet_Professional_P1102w?serial=000000000RK1HV44PR1a
direct usb://HP/LaserJet%20Professional%20P1102w?serial=000000000RK1HV44PR1a
network ipp
network ipps
network http
network https
network smb
direct hpfax

```

I have no idea what went wrong here and I am left with an unusable printer... If you notice anything, please let me know.

Best regards!

---

### Post by tgalati4 on 2015-09-19
How old is this printer?  Unfortunately, many HP consumer printers die an unexpected death.  Power supply issues, capacitor issues, CPU/motherboard issues, the list goes on.  Does your printer have an ethernet port?  Try using that instead of USB.  It's possible that the USB circuitry on the printer has gone bad, since the print engine works OK, but your log messages show USB disconnect.

Find another linux machine, or a Windows machine and try installing the printer.  If you can't print from either, then you can be reasonably sure that your printer is having a bad day.

---

### Post by ric_Poirier on 2015-09-19
Dear tgalati4,

Thanks for answering. The printer is around 4-5 years old, so your suggestion is relevant.
> 
...but your log messages show USB disconnect.

Would you be kind enough to tell me where in my output you have noticed this, please? It seems to me the computer knew that the printer was plugged/unplugged. Unfortunately, there are no ethernet ports, so I will try it on another computer first chance I get.

Thanks a lot.

---

### Post by pqwoerituytrueiwoq on 2015-09-19
> **ric_Poirier said:**
> Dear tgalati4,

Thanks for answering. The printer is around 4-5 years old, so your suggestion is relevant.

Would you be kind enough to tell me where in my output you have noticed this, please? It seems to me the computer knew that the printer was plugged/unplugged. Unfortunately, there are no ethernet ports, so I will try it on another computer first chance I get.

Thanks a lot.
after looking at them myself i found it however i think that was cause you unplugged the printer
im no printer expert, but id try printing from a live session (cd/usb boot) and the guest account
id guess some kind of print que issue or you are not printing to the printer you think you are
have you tried removing the printer and adding it again via software
*remove via software then unplug/plugging the usb cable should do it

---

### Post by ric_Poirier on 2015-09-19
pqwoerituytrueiwoq, thank you, it's a good idea. I'll try this first.

Regards,

---

### Post by tgalati4 on 2015-09-19
Yes, if the USB disconnect corresponds to you unplugging the printer, then that is OK and expected.  If the computer's USB port is failing, then you should see some indication of it in the syslog.  If the printer's CPU is failing, you will not get any messages except frustration.

Run *hp-toolbox* and keep a log of the device status as you try to print.

---

### Post by ric_Poirier on 2015-09-20
Hello guys, just a little follow up,

From tagalati4's suggestion, I installed hp-toolbox and from there, was able to print a test page from my computer. Furthermore, I was able to print my file from the tollbox's "Action" menu, but directly from the file (weird). I found an error log in cups, and in it, the following interesting lines:

```

D [19/Sep/2015:22:08:19 -0400] [Job 93] **** Warning:  Invalid Page count.
D [19/Sep/2015:22:08:19 -0400] [Job 93] **** Warning:  Invalid Page count.
D [19/Sep/2015:22:08:19 -0400] [Job 93] No pages will be processed (FirstPage > LastPage).
D [19/Sep/2015:22:08:19 -0400] [Job 93] **** This file had errors that were repaired or ignored.

```

The document I was trying to print shows a page count a 8 pages, although in reality, there are 11 pages (some of the first pages are not numbered). I guess the printer didn't know how to deal with that. Still, I was not able to print anything but test pages and documents from the hp-toolbox, which was annoying. So from the hp-toolbox, I reinstalled the printer from scratch, and everything started working again.

I tried the "broken" document again and was still not able to print it, but everything else prints fine.

Thanks for your help, I will mark this as solved.

---

