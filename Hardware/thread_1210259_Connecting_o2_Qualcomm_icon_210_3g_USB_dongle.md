---
title: "Connecting o2 Qualcomm icon 210 3g USB dongle"
date: 2009-07-11
forum: Hardware
---

### Post by smellydog on 2009-07-11
I am running Ubuntu Hardy with NM 0.6.  I am trying to connect my Qualcomm icon 210 that is a prepay 3G USB HSDPA/UMTS/GPRS modem from Germany, also known as the O2-LOOP-Surf-Stick 2.  This is a long thread, but I tried to include as much applicable info as possible.

I put my sim chip in a cell phone and disabled pin requirement, reinstalled sim chip into USB dongle (because some of the chatscripts used for pon require pin disabled)

<ifconfig prior to connection>
```
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d0:90:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100064 (97.7 KB)  TX bytes:100064 (97.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:27:fe:1e  
          inet addr:10.5.81.114  Bcast:10.5.81.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe27:fe1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:676 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42955 (41.9 KB)  TX bytes:15674 (15.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-27-FE-1E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


connected stick to usb port
icon 210 auto mounts and appears on desktop as usb memory storage device (also noticed a new scsi device that appears to be my modem as a scsi cd-rom... not sure, but i am sure i do not have a scsi cd-rom)

<lsusb output>
```
Bus 007 Device 002: ID 1e0e:f000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 003: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000
```

<dmesg output>
```
[  115.371553] usb 7-2: new high speed USB device using ehci_hcd and address 2
[  115.508162] usb 7-2: configuration #1 chosen from 1 choice
[  115.598614] usbcore: registered new interface driver libusual
[  115.607809] Initializing USB Mass Storage driver...
[  115.609101] scsi5 : SCSI emulation for USB Mass Storage devices
[  115.609808] usbcore: registered new interface driver usb-storage
[  115.609812] USB Mass Storage support registered.
[  115.609906] usb-storage: device found at 2
[  115.609908] usb-storage: waiting for device to settle before scanning
[  116.339567] usb-storage: device scan complete
[  116.341189] scsi 5:0:0:0: CD-ROM            ZCOPTION HSDPA Modem      2.31 PQ: 0 ANSI: 0
[  116.353325] sr1: scsi-1 drive
[  116.353429] sr 5:0:0:0: Attached scsi CD-ROM sr1
[  116.353508] sr 5:0:0:0: Attached scsi generic sg2 type 5
```


I right click and eject memory stick or run "sudo usb_modeswitch" in terminal
-- device shows as USB Device 1e0e:9000 (USB modem)
---  If I right click an eject, the icon on the desktop disappears.  If i use usb_modeswitch, the icon stays but is empty and will not disappear even after modem is disconnected.  Just FYI, not important.

<lsusb output>
```
Bus 007 Device 002: ID 1e0e:f000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 003: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000
```

<dmesg output>
```
[  115.371553] usb 7-2: new high speed USB device using ehci_hcd and address 2
[  115.508162] usb 7-2: configuration #1 chosen from 1 choice
[  115.598614] usbcore: registered new interface driver libusual
[  115.607809] Initializing USB Mass Storage driver...
[  115.609101] scsi5 : SCSI emulation for USB Mass Storage devices
[  115.609808] usbcore: registered new interface driver usb-storage
[  115.609812] USB Mass Storage support registered.
[  115.609906] usb-storage: device found at 2
[  115.609908] usb-storage: waiting for device to settle before scanning
[  116.339567] usb-storage: device scan complete
[  116.341189] scsi 5:0:0:0: CD-ROM            ZCOPTION HSDPA Modem      2.31 PQ: 0 ANSI: 0
[  116.353325] sr1: scsi-1 drive
[  116.353429] sr 5:0:0:0: Attached scsi CD-ROM sr1
[  116.353508] sr 5:0:0:0: Attached scsi generic sg2 type 5
[  170.888667] usb 7-2: USB disconnect, address 2
[  171.035097] usb 7-2: new high speed USB device using ehci_hcd and address 3
[  171.173893] usb 7-2: configuration #1 chosen from 1 choice
```

<ifconfig output>
is still the same as previous. No change.
Device now is discovered as a modem (I think)


I run the command in terminal <sudo modprobe usbserial vendor=0x1e0e product=0x9000>
this attaches usbserial driver to modem and three new ports are created.  ttyUSB0, ttyUSB1, ttyUSB2

<dmesg output>
```
[  115.371553] usb 7-2: new high speed USB device using ehci_hcd and address 2
[  115.508162] usb 7-2: configuration #1 chosen from 1 choice
[  115.598614] usbcore: registered new interface driver libusual
[  115.607809] Initializing USB Mass Storage driver...
[  115.609101] scsi5 : SCSI emulation for USB Mass Storage devices
[  115.609808] usbcore: registered new interface driver usb-storage
[  115.609812] USB Mass Storage support registered.
[  115.609906] usb-storage: device found at 2
[  115.609908] usb-storage: waiting for device to settle before scanning
[  116.339567] usb-storage: device scan complete
[  116.341189] scsi 5:0:0:0: CD-ROM            ZCOPTION HSDPA Modem      2.31 PQ: 0 ANSI: 0
[  116.353325] sr1: scsi-1 drive
[  116.353429] sr 5:0:0:0: Attached scsi CD-ROM sr1
[  116.353508] sr 5:0:0:0: Attached scsi generic sg2 type 5
[  170.888667] usb 7-2: USB disconnect, address 2
[  171.035097] usb 7-2: new high speed USB device using ehci_hcd and address 3
[  171.173893] usb 7-2: configuration #1 chosen from 1 choice
[  256.990047] usbcore: registered new interface driver usbserial
[  256.990085] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  256.990168] usbserial_generic 7-2:1.0: generic converter detected
[  256.990386] usb 7-2: generic converter now attached to ttyUSB0
[  256.990404] usbserial_generic 7-2:1.1: generic converter detected
[  256.990513] usb 7-2: generic converter now attached to ttyUSB1
[  256.990528] usbserial_generic 7-2:1.2: generic converter detected
[  256.990639] usb 7-2: generic converter now attached to ttyUSB2
[  256.990658] usbcore: registered new interface driver usbserial_generic
[  256.990663] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
```

<ifconfig output>
```
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d0:90:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100064 (97.7 KB)  TX bytes:100064 (97.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:27:fe:1e  
          inet addr:10.5.81.114  Bcast:10.5.81.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe27:fe1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141620 (138.3 KB)  TX bytes:16970 (16.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-27-FE-1E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```


From here is the problem.

I have tried <sudo umtsmon -s /dev/ttyUSB2,/dev/ttyUSB2>.  Does not get past registering device and does not dial out as far as i can tell.
<terminal output while running>
```
umtsmon version 0.9.71 .
##P1 t=478: Set suggested AT port to '/dev/ttyUSB2'
##P1 t=478: Set suggested PPP port to '/dev/ttyUSB2'
installing GUI SIGABRT handler
##P1 t=481: umtsmon is running as root!!!
```

I tried wvdial
I ran sudo wvdialconf and edited the scripts in /etc/wvdial.conf to include the phone number (*99#) and APN (surfo2) with a couple of other commands.

<my wvdial.conf contents>
```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Stupid Mode = 1
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB1
ISDN = 0
; Phone = <Target Phone Number>
Password = o2
Username = o2

[Dialer o2]
Dial Command = ATDT
Phone = *98#
Init = AT+CGDCONT=1,"IP","surfo2"
```


This is the output from running <wvdial o2>

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CGDCONT=1,"IP","surfo2"
AT+CGDCONT=1,"IP","surfo2"
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*98#
--> Waiting for carrier.
ATDT*98#
--> Disconnecting at Sat Jul 11 07:31:23 2009
```

Also after running wvdial, it disconnects my usb dongle and reappears as the usb memory stick.

<lsusb output>
```
Bus 007 Device 004: ID 1e0e:f000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 003: ID 0a5c:2110 Broadcom Corp. 
Bus 001 Device 001: ID 0000:0000
```


I have also used <pon> with the scripts as suggested in these two web pages.
[http://cluster.physik.uni-freiburg.de/~kuhnen/surfstick2/index.html](http://cluster.physik.uni-freiburg.de/~kuhnen/surfstick2/index.html)
[http://eeegadgets.blogspot.com/2009/04/howto-qualcomm-3g-icon-210-and-ubuntu.html](http://eeegadgets.blogspot.com/2009/04/howto-qualcomm-3g-icon-210-and-ubuntu.html)

My device did manage to make a successful connection one time.  The light switched from red, to steady blue, to blinking blue.  I disconnected and reconnected and it was fine.  I was able to log on again.  ifconfig showed a ppp0 interface assigned to USB2,  i was happy and excited.  After a reboot, ppp0 never showed up again and all i get is headaches.  I even tried my chip in a sony ericson w810i cell phone.  It also connected ONE TIME.  Again after a reboot, never again.  Just for information, both devices work on Windo$e.  I went down to the store where i bought the USB dongle and it works there too.

I am at a loss.

I must be missing something simple.  I must be overlooking SOMETHING.  

I appreciate any guidance.

---

### Post by GeorgeVita on 2009-07-11
Hi **smellydog**,
looking at your /etc/wvdial.conf you have a wrong dial number (*98#).
Use **sudo gedit /etc/wvdial.conf** and edit your file to be:
```
[Dialer Defaults]
Modem = /dev/ttyUSB1
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Username = o2
Password = o2
Phone = *99#
Stupid Mode = 1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","surfo2"

[Dialer 0]
Modem = /dev/ttyUSB0

[Dialer 1]
Modem = /dev/ttyUSB1

[Dialer 2]
Modem = /dev/ttyUSB2
```
Dial using **sudo wvdial** and remove "offline mode" from firefox with **ALT-F W**

Post here any results to follow up.

EDIT: I used /dev/ttyUSB1 as your tries, phone=*99# (not *98# as you mistyped) and named Init**3** the APN setting line. You can try **sudo wvdial 2** to try /dev/ttyUSB2 port. 

Regards,
George

---

### Post by smellydog on 2009-07-11
This is my new wvdial.conf
```
[Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Password = o2
Username = o2
Phone = *99#
Stupid Mode = 1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init = AT+CGDCONT=1,"IP","surfo2"
```

I now type "sudo wvdial" in terminal

```
name@host:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CGDCONT=1,"IP","surfo2"
AT+CGDCONT=1,"IP","surfo2"
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 115200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jul 11 08:50:25 2009
--> Pid of pppd: 7179
--> Using interface ppp0
--> pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: 0&#65533;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Sat Jul 11 08:51:02 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
```

I can see that it is a step closer!  But still no go.  Last time I remember from the successful log on, when i used the command "modprobe" to attached the usbserial driver, the USB modem light went from solid red to solid blue (I am assuming that is when ppp0 was created and attached to ttyUSB2)?  When I invoked any scripts (with pon or wvdial...) to sign on to the o2 server, it went to a blinking blue and I had the primary and secondary DNS servers listed in the terminal.  From this edit to my wvdial.conf, I can see that it at least started PPP, but there was still no ppp0 listed from the command ifconfig.  If that makes any sense.

This is helpful, thanks.

---

### Post by smellydog on 2009-07-11
This is a snapshot of my syslog

Jul 11 08:41:35 LenovoT61 kernel: [   72.387913] usbcore: registered new interface driver usbserial
Jul 11 08:41:35 LenovoT61 kernel: [   72.387928] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Jul 11 08:41:35 LenovoT61 kernel: [   72.387963] usbserial_generic 2-2:1.0: generic converter detected
Jul 11 08:41:35 LenovoT61 kernel: [   72.388052] usb 2-2: generic converter now attached to ttyUSB0
Jul 11 08:41:35 LenovoT61 kernel: [   72.388059] usbserial_generic 2-2:1.1: generic converter detected
Jul 11 08:41:35 LenovoT61 kernel: [   72.388103] usb 2-2: generic converter now attached to ttyUSB1
Jul 11 08:41:35 LenovoT61 kernel: [   72.388110] usbserial_generic 2-2:1.2: generic converter detected
Jul 11 08:41:35 LenovoT61 kernel: [   72.388153] usb 2-2: generic converter now attached to ttyUSB2
Jul 11 08:41:35 LenovoT61 kernel: [   72.388161] usbcore: registered new interface driver usbserial_generic
Jul 11 08:41:35 LenovoT61 kernel: [   72.388163] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Jul 11 08:41:35 LenovoT61 NetworkManager: <debug> [1247316095.510342] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1e0e_9000_noserial_if0_serial_usb_0'). 
Jul 11 08:41:35 LenovoT61 NetworkManager: <debug> [1247316095.513983] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1e0e_9000_noserial_if1_serial_usb_1'). 
Jul 11 08:41:35 LenovoT61 NetworkManager: <debug> [1247316095.515354] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1e0e_9000_noserial_if2_serial_usb_2'). 
Jul 11 08:49:59 LenovoT61 pppd[7124]: pppd 2.4.4 started by saverio, uid 1000
Jul 11 08:49:59 LenovoT61 kernel: [  174.337855] PPP generic driver version 2.4.2
Jul 11 08:49:59 LenovoT61 pppd[7124]: Using interface ppp0
Jul 11 08:49:59 LenovoT61 pppd[7124]: Connect: ppp0 <--> /dev/ttyUSB2
Jul 11 08:49:59 LenovoT61 pppd[7124]: PAP authentication succeeded
Jul 11 08:49:59 LenovoT61 kernel: [  174.425046] PPP BSD Compression module registered
Jul 11 08:49:59 LenovoT61 kernel: [  174.461892] PPP Deflate Compression module registered
Jul 11 08:50:11 LenovoT61 pppd[7124]: Terminating on signal 15
Jul 11 08:50:25 LenovoT61 pppd[7179]: pppd 2.4.4 started by root, uid 0
Jul 11 08:50:25 LenovoT61 pppd[7179]: Using interface ppp0
Jul 11 08:50:25 LenovoT61 pppd[7179]: Connect: ppp0 <--> /dev/ttyUSB2
Jul 11 08:50:25 LenovoT61 pppd[7179]: CHAP authentication succeeded
Jul 11 08:50:25 LenovoT61 pppd[7179]: CHAP authentication succeeded
Jul 11 08:50:55 LenovoT61 pppd[7179]: IPCP: timeout sending Config-Requests 
Jul 11 08:51:01 LenovoT61 pppd[7179]: Connection terminated.
Jul 11 08:51:01 LenovoT61 pppd[7179]: Modem hangup
Jul 11 08:51:01 LenovoT61 pppd[7179]: Exit.
Jul 11 08:51:07 LenovoT61 pppd[7210]: pppd 2.4.4 started by root, uid 0
Jul 11 08:51:07 LenovoT61 pppd[7210]: Using interface ppp0
Jul 11 08:51:07 LenovoT61 pppd[7210]: Connect: ppp0 <--> /dev/ttyUSB2
Jul 11 08:51:07 LenovoT61 pppd[7210]: CHAP authentication succeeded
Jul 11 08:51:07 LenovoT61 pppd[7210]: CHAP authentication succeeded
Jul 11 08:51:37 LenovoT61 pppd[7210]: IPCP: timeout sending Config-Requests 
Jul 11 08:51:43 LenovoT61 pppd[7210]: Connection terminated.
Jul 11 08:51:43 LenovoT61 pppd[7210]: Modem hangup
Jul 11 08:51:43 LenovoT61 pppd[7210]: Exit.
Jul 11 08:51:54 LenovoT61 pppd[7245]: pppd 2.4.4 started by root, uid 0
Jul 11 08:51:54 LenovoT61 pppd[7245]: Using interface ppp0
Jul 11 08:51:54 LenovoT61 pppd[7245]: Connect: ppp0 <--> /dev/ttyUSB2
Jul 11 08:51:54 LenovoT61 pppd[7245]: CHAP authentication succeeded
Jul 11 08:51:54 LenovoT61 pppd[7245]: CHAP authentication succeeded
Jul 11 08:52:24 LenovoT61 pppd[7245]: IPCP: timeout sending Config-Requests 
Jul 11 08:52:30 LenovoT61 pppd[7245]: Connection terminated.
Jul 11 08:52:30 LenovoT61 pppd[7245]: Modem hangup
Jul 11 08:52:30 LenovoT61 pppd[7245]: Exit.
Jul 11 08:52:51 LenovoT61 pppd[7308]: pppd 2.4.4 started by root, uid 0
Jul 11 08:52:51 LenovoT61 pppd[7308]: Using interface ppp0
Jul 11 08:52:51 LenovoT61 pppd[7308]: Connect: ppp0 <--> /dev/ttyUSB2
Jul 11 08:52:51 LenovoT61 pppd[7308]: CHAP authentication succeeded
Jul 11 08:52:51 LenovoT61 pppd[7308]: CHAP authentication succeeded
Jul 11 08:53:21 LenovoT61 pppd[7308]: IPCP: timeout sending Config-Requests 
Jul 11 08:53:27 LenovoT61 pppd[7308]: Connection terminated.
Jul 11 08:53:27 LenovoT61 pppd[7308]: Modem hangup
Jul 11 08:53:27 LenovoT61 pppd[7308]: Exit.

---

### Post by GeorgeVita on 2009-07-11
I think your setting are almost correct. i found 2 APNs from network Manager 0.7 (choose appropriate):

Germany, o2 (pay-by-time): **surfo2**
Germany, o2 (pay-by-MB): **internet**

Check also with Ethernet disconnected and wireless disabled (just in case of conflicts). Reboot before trying.

There are many ways to connect, so when you find out the setup parameters you may choose the appropriate to you!

EDIT: **usbserial** is just the usb to serial communication port driver. usb_modeswitch turn the device to the actual modem state (which can be usbserial-lised). At this point the problem seems to be just after negotiation with your provider for your account or a conflict from ppp dialler into the system

Searching to find other parameters needed...

---

### Post by GeorgeVita on 2009-07-11
Hi again, I did not found something specific.
Just check contents of a file regarding pppd and wvdial with the following:
```
sudo cat /etc/ppp/peers/wvdial
```

The contents of my file with working wvdial are:
```
noauth
name wvdial
usepeerdns
```

G

---

### Post by smellydog on 2009-07-11
This is what I have in my /etc/usb_modswitch.conf

```
########################################################
# Option iCON 210
# PROLiNK PHS100 (various looks)
# Hyundai Mobile MB-810
#
# One report of switching with DetachStorageOnly. Needs at least
# a second to settle before binding to usbserial
#
# Contributor: wahlm, Peter Kraker, Pakdhetimin Sekum

DefaultVendor=  0x1e0e
DefaultProduct= 0xf000

TargetVendor=   0x1e0e
TargetProduct=  0x9000
TargetClass=    0xff

# only for reference
MessageEndpoint=0x01

MessageContent="555342431234567800000000000006bd000000020000000000000000000000"

ResponseEndpoint=0x01


#######################################################
```


This is what I fixed my /etc/wvdial.conf to look like

```
[Dialer Defaults]
Modem = /dev/ttyUSB1
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Password = o2
Username = o2
Phone = *99#
Stupid Mode = 1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","surfo2"

[Dialer 0]
Modem = /dev/ttyUSB0

[Dialer 1]
Modem = /dev/ttyUSB1

[Dialer 2]
Modem = /dev/ttyUSB2
```

This is the result of ifconfig after disabling wlan0 and eth0

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119949 (117.1 KB)  TX bytes:119949 (117.1 KB)
```


I tried wvdial, wvdial 1 and wvdial 2.   The first two disconnected the modem and turned it back into a memory stick.  The wvdial 2 is the only one that stayed the same from previous entry with APN "surfo2, and APN "internet".  I tried both APN's with wlan0 and eth0 up and down with the wvdial 2 connection script.  I am going to try this new script with my phone and see what happens just to see out of curiosity.

the results of sudo cat /etc/ppp/peers/wvdial are the same as yours

---

### Post by smellydog on 2009-07-11
I tried my o2 chip in my phone.  It uses port ttyACM0 and ttyACM1.  I just added two more Dialers to the bottom of wvdial.conf as [Dialer 3] and [Dialer 4]

I used "sudo wvdial 3" so that it used ttyACM0, and it is connected

This is the output

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","surfo2"
AT+CGDCONT=1,"IP","surfo2"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&X*}3cD7~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jul 11 10:34:20 2009
--> Pid of pppd: 9924
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> local  IP address 10.70.130.224
--> pppd: &#65533;&#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;[06][08]
--> primary   DNS address 193.189.244.205
--> pppd: &#65533;&#65533;[06][08]
--> secondary DNS address 193.189.244.197
--> pppd: &#65533;&#65533;[06][08]
```



This is 'ifconfig'

```
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d0:90:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123165 (120.2 KB)  TX bytes:123165 (120.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.70.130.224  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:58 (58.0 B)  TX bytes:85 (85.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:27:fe:1e  
          inet addr:10.5.81.114  Bcast:10.5.81.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe27:fe1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1279 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1080602 (1.0 MB)  TX bytes:288367 (281.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-27-FE-1E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

I have a ppp0.

I suppose this eliminates the wvdial script.    I have to turn off my wlan0 and eth0 to use the phone.  the phone is not a 3g phone so it is considerably slower than what i am using at the moment.

---

### Post by GeorgeVita on 2009-07-11
Hi again,

I think that usb_modeswitch and the usbserial driver are OK.
You should use the /dev/ttyUSB2 once! (I mean only one program will use it).
Do not try pon/wvdial/... all together. If a program 'stucks' it will hold the port. As you have connected with /dev/ttyUSB2 once keep this.

The idea is to determine if your provider or the system 'cuts' the connection.

Be sure by asking 'technical support' of your provider about APN/user/pass (a wrong one may cost you more!).

Regards,
George

---

### Post by smellydog on 2009-07-11
I am not sure what the init2 string all means, but how come it works and the other one that was in there previously didn't?

thanks for your help George.  I very much appreciate it all

---

### Post by GeorgeVita on 2009-07-11
Till now you are connecting with the phone using the /etc/wvdial.conf via port /dev/ttyACM0 You can see valid IP and DNS numbers.

About Init2 command: AT&F E1 V1 X1 &D2 &C1 S0=0
**AT&F** is most important as it restores factory settings for the modem. You can have the same 'starting' position and work in various O.S. Others set command echo=ON, verbal responds, H/W handshake and no answer to any incoming call.

In your 1st try the main problem was the wrong dial number (*98#).

Now the problem must be interfacing with the USB modem.
**Exit code = 16** most times comes from a 'physical' h/w disconnection of the modem or when the provider hangs you up.

Just to leave the h/w possibility can you check another USB port?

EDIT: ... last try to add the following to **/etc/ppp/peers/wvdial** file:
mtu 1452
mru 1452
and use **115200** as Baud rate (as stated to a lot of links)
see also: [http://forum.ubuntuusers.de/topic/o2-surfstick-qualcomm-3g-icon-210-unter-ubunt/?highlight=qualcomm](http://forum.ubuntuusers.de/topic/o2-surfstick-qualcomm-3g-icon-210-unter-ubunt/?highlight=qualcomm)


G

---

### Post by smellydog on 2009-07-11
Thanks George.  I took your advice with the APN settings, but since it is past business hours here in Germany I did the next best thing I could think of.

I looked up the APN and Dial out number on my friends windowse computer.  The dialer that was used on windowse gave me an APN of "pinternet.interkom.de" and phone number of "*98#".

I tried it on my cell phone as a modem and it connects with those settings in wvdial.conf.  I get the same primary and secondary DNS address as before, but the Local IP I believe is Dynamic because it changes everytime I reconnect.  

I put my chip back in my USB stick and tried another USB port like you suggested and it does not work.  I attached output below.

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","pinternet.interkom.de"
AT+CGDCONT=1,"IP","pinternet.interkom.de"
OK
--> Modem initialized.
--> Sending: ATDT*98#
--> Waiting for carrier.
ATDT*98#
CONNECT 115200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jul 11 12:17:34 2009
--> Pid of pppd: 7508
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> Disconnecting at Sat Jul 11 12:18:11 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

What I do not understand is that this thing was working once, so I know that it works!  This is just too weird.  Is it possible that after plugging it in my friends windose that it could have written something to the USB stick changing the firmware or something?  Because when it was a windows virgin was the last time it worked on Linux... just a thought.  I do know that it should work in whatever computer you plug it in.

Kris

---

### Post by smellydog on 2009-07-11
Changed /etc/ppp/peers/wvdial to the following

```
noauth
name wvdial
usepeerdns
[B]mtu 1452
mru 1452[/B]
```


Changed /etc/wvdial.conf to the following

```
[Dialer Defaults]
Modem = /dev/ttyUSB1
Modem Type = Analog Modem
ISDN = 0
Baud = **115200**
Password = o2
Username = o2
Phone = *98#
Stupid Mode = 1
Init1 = ATZ
Init2 = AT&F E1 V1 X1 &D2 &C1 S0=0
Init3 = AT+CGDCONT=1,"IP","pinternet.interkom.de"

[Dialer 0]
Modem = /dev/ttyUSB0

[Dialer 1]
Modem = /dev/ttyUSB1

[Dialer 2]
Modem = /dev/ttyUSB2

[Dialer 3]
Modem = /dev/ttyACM0

[Dialer 4]
Modem = /dev/ttyACM1
```


I ran "sudo wvdial 2" in terminal

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: AT&F E1 V1 X1 &D2 &C1 S0=0
AT&F E1 V1 X1 &D2 &C1 S0=0
OK
--> Sending: AT+CGDCONT=1,"IP","pinternet.interkom.de"
AT+CGDCONT=1,"IP","pinternet.interkom.de"
OK
--> Modem initialized.
--> Sending: ATDT*98#
--> Waiting for carrier.
ATDT*98#
CONNECT 115200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Jul 11 12:51:02 2009
--> Pid of pppd: 7256
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]
--> Disconnecting at Sat Jul 11 12:51:38 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

---

### Post by GeorgeVita on 2009-07-11
Hi again,
in your /etc/wvdial.conf you can add another line: [B]Dial Attempts = 1
[/B]
just to try once (it must connect from the first try).

Reading all your posts, you have connected with one (which?) method? The most possible if from the links:> I have also used <pon> with the scripts as suggested in these two web pages.
[http://cluster.physik.uni-freiburg.d...ck2/index.html](http://cluster.physik.uni-freiburg.d...ck2/index.html)
[http://eeegadgets.blogspot.com/2009/...nd-ubuntu.html](http://eeegadgets.blogspot.com/2009/...nd-ubuntu.html)

Can you try step by step again these instructions? Do not fear/change usb_modeswitch as you have the /dev/ttyUSB2 port working.

Regards,
George

---

### Post by smellydog on 2009-07-12
Hello George

I re accomplished all my scripts as per the suggestion of the two web sites I cited earlier in my posting (#1).  The one from the web page
[http://cluster.physik.uni-freiburg.de/~kuhnen/surfstick2/index.html](http://cluster.physik.uni-freiburg.de/~kuhnen/surfstick2/index.html)
does not have any terminal output, so I pasted my results from my syslog

```
Jul 12 07:04:25 LenovoT61 pppd[11279]: pppd 2.4.4 started by root, uid 0
Jul 12 07:04:26 LenovoT61 chat[11281]: report (CONNECT)
Jul 12 07:04:26 LenovoT61 chat[11281]: abort on (BUSY)
Jul 12 07:04:26 LenovoT61 chat[11281]: abort on (NO CARRIER)
Jul 12 07:04:26 LenovoT61 chat[11281]: abort on (NO DIALTONE)
Jul 12 07:04:26 LenovoT61 chat[11281]: send (ATZ^M)
Jul 12 07:04:26 LenovoT61 chat[11281]: expect (OK)
Jul 12 07:04:26 LenovoT61 chat[11281]: ATZ^M^M
Jul 12 07:04:26 LenovoT61 chat[11281]: OK
Jul 12 07:04:26 LenovoT61 chat[11281]:  -- got it 
Jul 12 07:04:26 LenovoT61 chat[11281]: send (ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0^M)
Jul 12 07:04:26 LenovoT61 chat[11281]: expect (OK)
Jul 12 07:04:26 LenovoT61 chat[11281]: ^M
Jul 12 07:04:26 LenovoT61 chat[11281]: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0^M^M
Jul 12 07:04:26 LenovoT61 chat[11281]: OK
Jul 12 07:04:26 LenovoT61 chat[11281]:  -- got it 
Jul 12 07:04:26 LenovoT61 chat[11281]: send (AT+CGDCONT=1,"IP","surfo2"^M)
Jul 12 07:04:26 LenovoT61 chat[11281]: expect (OK)
Jul 12 07:04:26 LenovoT61 chat[11281]: ^M
Jul 12 07:04:26 LenovoT61 chat[11281]: AT+CGDCONT=1,"IP","surfo2"^M^M
Jul 12 07:04:26 LenovoT61 chat[11281]: OK
Jul 12 07:04:26 LenovoT61 chat[11281]:  -- got it 
Jul 12 07:04:26 LenovoT61 chat[11281]: send (ATD*99#^M)
Jul 12 07:04:26 LenovoT61 chat[11281]: expect (CONNECT)
Jul 12 07:04:26 LenovoT61 chat[11281]: ^M
Jul 12 07:04:26 LenovoT61 chat[11281]: ATD*99#^M^M
Jul 12 07:04:26 LenovoT61 chat[11281]: CONNECT
Jul 12 07:04:26 LenovoT61 chat[11281]:  -- got it 
Jul 12 07:04:26 LenovoT61 pppd[11279]: Serial connection established.
Jul 12 07:04:26 LenovoT61 pppd[11279]: Using interface ppp0
Jul 12 07:04:26 LenovoT61 pppd[11279]: Connect: ppp0 <--> /dev/ttyUSB2
Jul 12 07:04:27 LenovoT61 pppd[11279]: PAP authentication succeeded
Jul 12 07:04:57 LenovoT61 pppd[11279]: IPCP: timeout sending Config-Requests 
Jul 12 07:05:03 LenovoT61 pppd[11279]: Connection terminated.
Jul 12 07:05:04 LenovoT61 pppd[11279]: Modem hangup
Jul 12 07:05:04 LenovoT61 pppd[11279]: Exit.
```

The other scripts suggested by the second web site is identical to the first.  I do know that the script says to have an APN of "surfo2" and dial "99" in the output above, I did change it a few times to experiment with the other successful APN's and dial of "98" and still the same result.  

[http://eeegadgets.blogspot.com/2009/04/howto-qualcomm-3g-icon-210-and-ubuntu.html](http://eeegadgets.blogspot.com/2009/04/howto-qualcomm-3g-icon-210-and-ubuntu.html)

I tried with the wlan0/eth0 up and down.  The outcome was the same.

I was poking around in the /etc/udev/rules.d/ and found that in rule 60-symlinks.rules has the ports of ttyUSB* associated to Handspring and Palm pilot devices??  I am not to clear how the rules work.  But from what you have put in the wvdial.conf script, the ttyACM port works and connects with my cell phone, but the ttyUSB does not.  Using identical settings on both modems, using the same sim card, the only difference is the hardware and the ports.  At least you got my phone to consistently connect!

Kris

---

### Post by GeorgeVita on 2009-07-12
Hi **Kris**,
we both will become more happy if you succeed to connect with the USB modem! (and understand where was the problem...)

For self educating on **udev** take a look at:
[http://ubuntuforums.org/showpost.php?p=3032927](http://ubuntuforums.org/showpost.php?p=3032927)
(there are many pages from wiki or help but there are real applications!)

**udev rules** are executed only when the device is attached, so do not 'read' other rules as you are not using the specific peripheral. A problem could exist if the manufacturer of the modem uses the same IDs for another product with different USB port behaviour.

With previous versions of Ubuntu. some HAL definition files had the data for modems and sometimes these are conflicting with udev rules. At recent version (9.04) network manager and kernel are trying to 'drive' the modem ...

For your case this is our search string now: **IPCP: timeout sending Config-Requests**

This can be caused also because your provider closed the data connection, so APN and user password must be checked. If you can retrieve them from the GSM phone it will be the same! Can you use the phone's connection and install **minicom**?

G

---

### Post by smellydog on 2009-07-12
ok, I hooked up my phone.  I didn't connect at first so I did the following

I ran "ifconfig" to get the IP address from ppp0
```
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d0:90:a8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3009 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:136891 (133.6 KB)  TX bytes:136891 (133.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.40.72.184  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1452  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:58 (58.0 B)  TX bytes:85 (85.0 B)
```

then I ran this to change the gw from wlan0 to ppp0
```
sudo route add default gw 10.40.72.184
```

I successfully downloaded/installed **minicom** from synaptic from the phone

---

### Post by GeorgeVita on 2009-07-12
You are going to use **minicom** to 'investigate' your phones data.

0. you dnld **minicom** via Synaptic Package Manager
1. you must be **disconnected** to test the following!
2. open a terminal window: **minicom -s**
3. choose **Serial port setup**
4. **A-** ... **/dev/ttyACM0**
...(or /dev/ttyUSB2 for your USB modem)
5. press **ESC**
6. choose **Modem and dialling**
7. edit **A** to become: **~^M~AT^M**
8. **delete all** contents into **B**
9. press **ESC**
10. press **ESC**

Into **minicom** press **CTRL-A Z** to see the MENU or **CTRL-A X** and **Yes** to EXIT. 

Type **AT** and press <enter>. You must see **OK**
Type **ATE1** and press <enter> to have 'echo on', you must see **OK**
From now type in **lower case**. All responds are in UPPER CASE and will be easier to understand what is going on. Every command is followed by an <enter> key.
Try **at+csq** you will get the signal strength (GSM mode).
Try **ati** to get phones/modem identification info.
**at&v** to see all 'now working' setup parameters.
and finally **at+cgdcont?** to get the desired APN!

**[COLOR="Red"]NOTE:[/COLOR]** some commands may 'change' settings and make it difficult to return! First understand then try! Here I must write: "Test at your own risk!"

**atz** is a software reset
**at&f** restores factory settings

Some others control SMS send/receive/store etc. I will try to find a link just to become more technical...we are going "off topic" from this thread but I think it is interesting.

G

---

### Post by smellydog on 2009-07-12
Hello again

Here are the results from your instructions

```
Welcome to minicom 2.3-rc1                                                     
                                                                               
OPTIONS: I18n                                                                  
Compiled on Dec 10 2007, 10:36:19.                                             
Port /dev/ttyUSB2                                                              
                                                                               
                 Press CTRL-A Z for help on special keys                       
                                                                               
AT                                                                             
OK                                                                             
ATE1                                                                           
OK                                                                             
at+csq                                                                         
+CSQ: 99,99                                                                    
                                                                               
OK                                                                             
ati                                                                            
Manufacturer: Option N.V.                                                      
Model: iCON 210                                                                
Revision: I: P3.2 QCT_23_V40_2_081128_0_H1  1  [Nov 28 2008 11:11:33]          
IMEI: I: xxxxxxxxxxxxxxx                                                     
+GCAP: +CGSM,+FCLASS,+DS                                                       
                                                                                
OK                                                                              
at&v                                                                            
&C: 2; &D: 2; &E: 1; &F: 0; &S: 0; &W: 0; E: 1; L: 0; M: 0; Q: 0; V: 1;         
X: 0; Z: 0; \Q: 3; \S: 0; \V: 0; O: 0; S0: 0; S2: 43; S3: 13; S4: 10;           
S5: 8; S6: 2; S7: 50; S8: 2; S9: 6; S10: 14; S11: 95; S30: 0; S103: 1;          
S104: 1; +FCLASS: 0; +ICF: 3,3; +IFC: 2,2; +IPR: 115200; +DR: 0;                
+DS: 0,0,2048,6; +WS46: 12; +CBST: 0,0,1;                                       
+CRLP: (61,61,48,6,0),(61,61,48,6,1),(240,240,52,6,2);                          
+CV120: 1,1,1,0,0,0; +CHSN: 0,0,0,0; +CSSN: 0,0; +CREG: 0; +CGREG: 0;           
+CFUN:; +CSCS: "IRA"; +CSTA: 129; +CR: 0; +CRC: 0; +CMEE: 2; +CGDCONT: (1,"IP",)
; ; +CGDSCONT: ; +CGTFT: ; +CGEQREQ: ; +CGEQMIN: ; +CGQREQ: ; +CGQMIN: ;        
+CGEREP: 0,0; +CGDATA: "PPP"; +CGCLASS: "A"; +CGSMS: 3; +CSMS: 0;               
+CMGF: 0; +CSAS: 0; +CRES: 0; +CSCA: "+491760000443",145; +CSMP: ,,0,0;         
+CSDH: 0; +CSCB: 0,"",""; +FDD: 0; +FAR: 0; +FCL: 0; +FIT: 0,0; +ES: ,,;        
+ESA: 0,,,,0,0,255,; +CMOD: 0; +CVHU: 1; +CPIN: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;,&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;;              
+CMEC: 0,0,0; +CKPD: 1,1; +CIND: 0,0,0,0,0,0,0,0; +CMER: 0,0,0,0,0;             
+CGATT: 0; +CGACT: 0; +CPBS: "SM"; +CPMS: "ME","ME","ME";                       
+CNMI: 0,0,0,0,0; +CMMS: 0; +FTS: 0; +FRS: 0; +FTH: 3; +FRH: 3; +FTM: 96;       
+FRM: 96; +CCUG: 0,0,0; +COPS: 0,0,""; +CUSD: 0; +CAOC: 1; +CCWA: 0;            
+VTS: 11; +CCLK: ""; +CLVL: 2; +CMUT: 1; +CPOL: 0,2,"",0,0,0; +CPLS: 0;         
+CTZR: 0; +CTZU: 0; +CLIP: 0; +COLP: 0; +CDIP: 0; +CLIR: 0; +CNAOP: 2;          
+CNSDP: 2; +CNSMOD: 0; +AUTOCSQ: 0; +CPSI: 0                                    
                                                                                
OK                                                                              
at+cgdcont                                                                      
OK                                                                              
at+cgdcont?                                                                     
+CGDCONT: 1,"IP","surfo2","0.0.0.0",0,0                                         
                                                                                
OK
```

---

### Post by GeorgeVita on 2009-07-12
do the same after connect/desconnect with the phone to check if respond to **at+cgdcont?** is the same!

---

### Post by smellydog on 2009-07-12
Here are the results from the phone as modem

```
Welcome to minicom 2.3-rc1                                                     
                                                                               
OPTIONS: I18n                                                                  
Compiled on Dec 10 2007, 10:36:19.                                             
Port /dev/ttyACM0                                                              
                                                                               
                 Press CTRL-A Z for help on special keys                       
                                                                               
AT                                                                             
OK                                                                             
ATE                                                                            
OK                                                                             
ATE1                                                                           
OK                                                                             
at+csq                                                                         
+CSQ: 29,99                                                                    
                                                                               
OK                                                                             
ati                                                                            
Sony Ericsson W810                                                             
                                                                               
OK                                                                             
at&v                                                                            
ERROR                                                                           
at+cgdcont?                                                                     
+CGDCONT: 1,"IP","pinternet.interkom.de","0.0.0.0",0,0                          
+CGDCONT: 2,"IP","pinternet.interkom.de","0.0.0.0",0,0                          
+CGDCONT: 3,"IP","pinternet.interkom.de","0.0.0.0",0,0                          
+CGDCONT: 4,"IP","pinternet.interkom.de","0.0.0.0",0,0                          
                                                                                
OK
```

---

### Post by GeorgeVita on 2009-07-12
> **smellydog said:**
> ...I looked up the APN and Dial out number on my friends windowse computer.  The dialer that was used on windowse gave me an APN of "pinternet.interkom.de" and phone number of "*98#".

I tried it on my cell phone as a modem and it connects with those settings in wvdial.conf...

What I do not understand is that this thing was working once, so I know that it works!  This is just too weird.  Is it possible that after plugging it in my friends windose that it could have written something to the USB stick changing the firmware or something?  Because when it was a windows virgin was the last time it worked on Linux... just a thought.  I do know that it should work in whatever computer you plug it in.

**AT&F** may cause this by restoring default settings. This command is 'a must' when you succeed the connection to a Linux system because other O.S. cannot alter 'factory' settings.

From your two previous posts, I saw +CSQ=99,99 (no signal) at the USB modem. Possibly it was temporary. If it looses the signal it will close the connection. I suppose also that you are using the same SIM card for your tests.

Also **sudo route add default gw 10.40.72.184** helps connecting with the phone ... the road is a dead end!

Below is the final /etc/wvdial.conf
```
[Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 115200
Password = o2
Username = o2
Phone = *99#
Stupid Mode = 1
Dial Attempts = 1
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","pinternet.interkom.de"

[Dialer W810]
Modem = /dev/ttyACM0
```

APN pinternet.interkom.de is for FONIC (?) with phone *99# but works either the *98# (confused!)

Above I restored Init2 in case you are going to test again after a successful connection with the winPC. APN must be checked tomorrow with your provider, as Phone#, user, password.
Dial Attempts = 1 to stop trying.

Last try: Reboot without the modem, wait for the system to load, insert the modem, wait to find a good signal, try **sudo wvdial** (with your phone will be **sudo wvdial W810**).

G

---

### Post by smellydog on 2009-07-12
To answer your question about my SIM card.  It is the same one.  I am swapping it between the USB dongle and the phone.  

I rebooted the computer.  Plugged in the modem.  Swapped functions on the USB dongle.  Ran modprobe.  And finally wvmdial

The latest and greatest results from your re-engineered script...
```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","pinternet.interkom.de"
AT+CGDCONT=1,"IP","pinternet.interkom.de"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Jul 12 11:24:49 2009
--> Pid of pppd: 7418
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Sun Jul 12 11:25:25 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

and the syslog
```
Jul 12 11:17:09 LenovoT61 kernel: [  108.332356] usbserial_generic 7-2:1.0: generic converter detected
Jul 12 11:17:09 LenovoT61 kernel: [  108.332451] usb 7-2: generic converter now attached to ttyUSB0
Jul 12 11:17:09 LenovoT61 kernel: [  108.332459] usbserial_generic 7-2:1.1: generic converter detected
Jul 12 11:17:09 LenovoT61 kernel: [  108.332503] usb 7-2: generic converter now attached to ttyUSB1
Jul 12 11:17:09 LenovoT61 kernel: [  108.332510] usbserial_generic 7-2:1.2: generic converter detected
Jul 12 11:17:09 LenovoT61 kernel: [  108.332566] usb 7-2: generic converter now attached to ttyUSB2
Jul 12 11:17:09 LenovoT61 kernel: [  108.332574] usbcore: registered new interface driver usbserial_generic
Jul 12 11:17:09 LenovoT61 kernel: [  108.332576] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
Jul 12 11:17:09 LenovoT61 NetworkManager: <debug> [1247411829.871655] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1e0e_9000_noserial_if0_serial_usb_0'). 
Jul 12 11:17:09 LenovoT61 NetworkManager: <debug> [1247411829.874208] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1e0e_9000_noserial_if1_serial_usb_1'). 
Jul 12 11:17:09 LenovoT61 NetworkManager: <debug> [1247411829.877169] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_1e0e_9000_noserial_if2_serial_usb_2'). 
Jul 12 11:17:14 LenovoT61 kernel: [  109.311113] PPP generic driver version 2.4.2
Jul 12 11:17:14 LenovoT61 pppd[7028]: pppd 2.4.4 started by root, uid 0
Jul 12 11:17:14 LenovoT61 pppd[7028]: Using interface ppp0
Jul 12 11:17:14 LenovoT61 pppd[7028]: Connect: ppp0 <--> /dev/ttyUSB2
Jul 12 11:17:14 LenovoT61 pppd[7028]: CHAP authentication succeeded
Jul 12 11:17:14 LenovoT61 pppd[7028]: CHAP authentication succeeded
Jul 12 11:17:14 LenovoT61 kernel: [  109.376033] PPP BSD Compression module registered
Jul 12 11:17:14 LenovoT61 kernel: [  109.421236] PPP Deflate Compression module registered
Jul 12 11:17:44 LenovoT61 pppd[7028]: IPCP: timeout sending Config-Requests 
Jul 12 11:17:50 LenovoT61 pppd[7028]: Connection terminated.
Jul 12 11:17:50 LenovoT61 pppd[7028]: Modem hangup
Jul 12 11:17:50 LenovoT61 pppd[7028]: Exit.
```

I will have to get back to this posting once I talk to the o2 reps.

Thank you very much for taking the time out of your day to help out with this.

Kris

---

### Post by GeorgeVita on 2009-07-12
Hi again,
reading again all links and your posts I have an idea covering:
> Jul 12 11:17:14 LenovoT61 kernel: [  109.376033] PPP BSD Compression module registered
Jul 12 11:17:14 LenovoT61 kernel: [  109.421236] PPP Deflate Compression module registered
Jul 12 11:17:44 LenovoT61 pppd[7028]: IPCP: timeout sending Config-Requests

As the timeout comes 30 seconds after compression, can we leave away this compression? Typically before this timeout occur IP and DNS must be provided.

Try this **sudo gedit /etc/ppp/peers/wvdial**
```
name wvdial
defaultroute
noipdefault
noauth
usepeerdns
novj
mtu 1452
mru 1452
ipcp-max-failure 60
```
(most comes from [http://forum.ubuntuusers.de/topic/o2-surfstick-qualcomm-3g-icon-210-unter-ubunt/](http://forum.ubuntuusers.de/topic/o2-surfstick-qualcomm-3g-icon-210-unter-ubunt/) )

Preferable to check both APNs, **wireless and ethernet disconnected.**

Regards,
George

---

### Post by smellydog on 2009-07-12
Hello

The new wvdial script
```
name wvdial
defaultroute
noipdefault
noauth
usepeerdns
novj
mtu 1452
mru 1452
ipcp-max-failure 60
```

Using the Qualcomm icon 210 on ttyUSB2.  Same output for both APN's
```
@LenovoT61:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","pinternet.interkom.de"
AT+CGDCONT=1,"IP","pinternet.interkom.de"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Jul 12 13:45:22 2009
--> Pid of pppd: 13908
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]&#65533;&#65533;[06][08]&#65533;&#65533;[06][08]
--> Disconnecting at Sun Jul 12 13:45:58 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

syslog
```
Jul 12 13:44:19 LenovoT61 pppd[13861]: pppd 2.4.4 started by saverio, uid 1000
Jul 12 13:44:19 LenovoT61 pppd[13861]: Using interface ppp0
Jul 12 13:44:19 LenovoT61 pppd[13861]: Connect: ppp0 <--> /dev/ttyUSB2
Jul 12 13:44:19 LenovoT61 pppd[13861]: CHAP authentication succeeded
Jul 12 13:44:19 LenovoT61 pppd[13861]: CHAP authentication succeeded
Jul 12 13:44:49 LenovoT61 pppd[13861]: IPCP: timeout sending Config-Requests 
Jul 12 13:44:55 LenovoT61 pppd[13861]: Connection terminated.
Jul 12 13:44:55 LenovoT61 pppd[13861]: Modem hangup
Jul 12 13:44:55 LenovoT61 pppd[13861]: Exit.
```

Connecting with W810 on ttyACM0.  Both APN's have identical results
```
LenovoT61:~$ sudo wvdial W810
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","surfo2"
AT+CGDCONT=1,"IP","surfo2"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&X*}3cD7~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Jul 12 13:55:17 2009
--> Pid of pppd: 14361
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> local  IP address 10.39.144.49
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> remote IP address 10.64.64.64
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> primary   DNS address 193.189.244.205
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
--> secondary DNS address 193.189.244.197
--> pppd: &#65533;&#65533;[06][08] &#65533;[06][08]
```

syslog
```
Jul 12 13:55:17 LenovoT61 pppd[14361]: pppd 2.4.4 started by root, uid 0
Jul 12 13:55:17 LenovoT61 pppd[14361]: Using interface ppp0
Jul 12 13:55:17 LenovoT61 pppd[14361]: Connect: ppp0 <--> /dev/ttyACM0
Jul 12 13:55:17 LenovoT61 pppd[14361]: CHAP authentication succeeded: Congratulations!
Jul 12 13:55:17 LenovoT61 pppd[14361]: CHAP authentication succeeded
Jul 12 13:55:18 LenovoT61 pppd[14361]: Could not determine remote IP address: defaulting to 10.64.64.64
Jul 12 13:55:18 LenovoT61 pppd[14361]: not replacing existing default route via 10.5.81.1
Jul 12 13:55:18 LenovoT61 pppd[14361]: Cannot determine ethernet address for proxy ARP
Jul 12 13:55:18 LenovoT61 pppd[14361]: local  IP address 10.39.144.49
Jul 12 13:55:18 LenovoT61 pppd[14361]: remote IP address 10.64.64.64
Jul 12 13:55:18 LenovoT61 pppd[14361]: primary   DNS address 193.189.244.205
Jul 12 13:55:18 LenovoT61 pppd[14361]: secondary DNS address 193.189.244.197
```

I performed both devices with both APN's and with eth0 and wlan0 disabled/off
syslog's and terminal outputs were the same regardles of APN and wlan0/eth0 settings.

Notice the two CHAP authentication succeeded lines for the two devices in the syslogs??  One has Congratulations! The other does not?

I also came across this post.
[http://ubuntuforums.org/showthread.php?t=1110616](http://ubuntuforums.org/showthread.php?t=1110616)
Would this have anything similar to my problem? 

I apologize if I know enough to be dangerous.

I also see what you mean about changing the default gw.  I connected without problems not doing that change.  What I did was I connected first and then turned off wlan0 and eth0.  This time I turned off wlan0 and eth0 first, THEN connected with the W810. Everything in good order I suppose.

---

### Post by GeorgeVita on 2009-07-12
> **smellydog said:**
> ...I also came across this post.
[http://ubuntuforums.org/showthread.php?t=1110616](http://ubuntuforums.org/showthread.php?t=1110616)
Would this have anything similar to my problem?

No, you have the /dev/ttyUSB2 you can connect but you cannot get IP and DNS from the provider. Either the system has them (wrong) or your provider does not supply them or the modem loops to another task like GPRS/3G switching.

The other idea with the 10-modem.fdi file can be used when the connection done, just to make automatic the usb-modeswitch and the usbserial port creation.

As you understand ... we need this connection! most cases are solved withing 2-4 posts some (as this one) could remain till trying next versions, something I did not proposed due to more problems: 
[http://ubuntuforums.org/showthread.php?t=1160081](http://ubuntuforums.org/showthread.php?t=1160081)

G

---

### Post by smellydog on 2009-07-22
[SOLVED]

I have my 3G Option Icon 210 working now.  I can not explain all what happened between last post and now.  I can tell you that what I did was is that i used an Acer Aspire One with linpus on it, removed that operating system and put Ubuntu 9.04 on it.  Not the netbook remix, the Desktop version.  I followed this wiki for the new version...
[http://wiki.ubuntuusers.de/Icon_210](http://wiki.ubuntuusers.de/Icon_210)

I plugged it in the Acer and the modem did exactly as it was described in the Wiki.  This time the blue light came on when I plugged it in and when I connected to the "web" the light started blinking.  It worked about two times without me changing any settings and then stopped connecting I suppose because of a conflict of interest with something internal... I don't know.  So after that I thought that I would give it a try in my lenovo.  Lo and behold the thing actually turned on at least.  I removed USB modeswitch and all the scripts and UDEV rules to try and see if anything was stopping it from turning the LED blue on the stick.  Nothing changed after a few reboots and resets.  So I reinstalled USB Modeswitch and Wvdial and all your scripts as you spelled out in this thread and I am connected now with it on my Lenovo.  So sorry to say, I don't know what the actuall issue was or is.  I am not confident that I will continue to connect with this piece of hardware, but I am taking advantage of it while I can.  Thanks for your Help George and sorry that I could not come up with a solution that pinpoints the problem.  My suspicion is that something is changing settings on the actual stick.  But I am no expert on this technology.

Thanks again.

---

