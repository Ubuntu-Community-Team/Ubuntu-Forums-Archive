---
title: "Problem connecting USB GPS SiRFStarIV NL-442U"
date: 2018-11-09
forum: Hardware
---

### Post by moromete on 2018-11-09
Hello,

I don't have Ubuntu or Kubuntu, I'm on KDE Neon

```
# inxi -Fx
System:    Host: romeo-All-Series Kernel: 4.15.0-38-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: KDE Plasma 5.14.0 (Qt 5.11.1) Distro: neon 16.04 xenial

```
Can't use USB GPS SiRFStarIV NL-442U

Before connect GPS in USB

```
# ls -l /dev/tty* | grep USB

# lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 413c:2107 Dell Computer Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

After connecting GPS in USB

```
#ls -l /dev/tty* | grep USB
crw-rw---- 1 root dialout 188,  0 nov  9 07:15 /dev/ttyUSB0

# lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 002: ID 413c:2107 Dell Computer Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

GPS USB: Bus 002 Device 006: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

# systemctl stop gpsd
Warning: Stopping gpsd.service, but it can still be activated by:
  gpsd.socket

# rm /var/run/gpsd.sock

# systemctl status gpsd
&#9679; gpsd.service - GPS (Global Positioning System) Daemon
   Loaded: loaded (/lib/systemd/system/gpsd.service; enabled; vendor preset: enabled)
   Active: inactive (dead) since Vi 2018-11-09 07:16:54 EET; 1min 26s ago
Main PID: 12029 (code=exited, status=0/SUCCESS)

nov 08 12:43:17 romeo-All-Series systemd[1]: Started GPS (Global Positioning System) Daemon.
nov 09 07:16:54 romeo-All-Series systemd[1]: Stopping GPS (Global Positioning System) Daemon...
nov 09 07:16:54 romeo-All-Series systemd[1]: Stopped GPS (Global Positioning System) Daemon.

#systemctl status gpsd.socket
&#9679; gpsd.socket - GPS (Global Positioning System) Daemon Sockets
   Loaded: loaded (/lib/systemd/system/gpsd.socket; enabled; vendor preset: enabled)
   Active: active (listening) since Jo 2018-11-08 12:43:17 EET; 18h ago
   Listen: /var/run/gpsd.sock (Stream)
           [::1]:2947 (Stream)
           127.0.0.1:2947 (Stream)
#systemctl stop gpsd.socket


#gpsmon /dev/ttyUSB0
/dev/ttyUSB0 4800 8N1         SiRF>
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;  X &#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Y  &#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Z  &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;  North &#9472;&#9472;&#9472;&#9472; East  &#9472;&#9472;&#9472;&#9472;&#9472; Alt  &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;Pos:  4107019  1734586  4546285 m       45.75222° 22.89661°      257 m        &#9474;
&#9474;Vel:      0.0      0.0      0.0 m/s          0.0       0.0       0.0 climb m/s&#9474;

```
From here: [http://catb.org/gpsd/troubleshooting.html](http://catb.org/gpsd/troubleshooting.html)

```
#gpsd -N -D3 -F /var/run/gpsd.sock
gpsd:INFO: launching (Version 3.15)
gpsd:INFO: listening on port gpsd
gpsd:INFO: running with effective group ID 20
gpsd:INFO: running with effective user ID 124
gpsd:INFO: startup at 2018-11-09T05:23:22.000Z (1541741002)
^Cgpsd:WARN: received terminating signal 2.
gpsd:WARN: exiting.
```

First step is OK !

```
#gpsd -N -D3 -F /var/run/gpsd.sock /dev/ttyUSB0
gpsd:INFO: launching (Version 3.15)
gpsd:INFO: listening on port gpsd
gpsd:INFO: stashing device /dev/ttyUSB0 at slot 0
gpsd:INFO: running with effective group ID 20
gpsd:INFO: running with effective user ID 124
gpsd:INFO: startup at 2018-11-09T05:25:41.000Z (1541741141)
^C*** buffer overflow detected ***: gpsd terminated
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x777e5)[0x7ff324c257e5]
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x5c)[0x7ff324cc715c]
/lib/x86_64-linux-gnu/libc.so.6(+0x117160)[0x7ff324cc5160]
/lib/x86_64-linux-gnu/libc.so.6(+0x1190a7)[0x7ff324cc70a7]

#gpsd -N -D3 -F /var/run/gpsd.sock /dev/ttyUSB0
gpsd:INFO: launching (Version 3.15)
gpsd:INFO: listening on port gpsd
gpsd:INFO: stashing device /dev/ttyUSB0 at slot 0
gpsd:INFO: running with effective group ID 20
gpsd:INFO: running with effective user ID 124
gpsd:INFO: startup at 2018-11-09T05:26:52.000Z (1541741212)

No gpsd: <= control(6): /dev/ttyUSB0 already active
```

From here: [http://catb.org/gpsd/troubleshooting.html#hotplugtroubleshooting](http://catb.org/gpsd/troubleshooting.html#hotplugtroubleshooting)

```
# tail -f /var/log/syslog
Nov  9 07:20:25 romeo-All-Series kernel: [605260.157706] pps pps0: source "/dev/ttyUSB0" added
Nov  9 07:21:10 romeo-All-Series org.kde.Spectacle[7044]: kf5.kio.core: Invalid URL: QUrl("Screenshot_20181109_072110.png")
Nov  9 07:21:10 romeo-All-Series org.kde.Spectacle[7044]: kf5.kio.core: Invalid URL: QUrl("Screenshot_20181109_072110.png")
Nov  9 07:21:39 romeo-All-Series org.kde.Spectacle[7044]: qt.qpa.xcb: QXcbConnection: XCB error: 3 (BadWindow), sequence: 4989, resource id: 38416588, major code: 40 
(TranslateCoords), minor code: 0
.....
Nov  9 07:31:11 romeo-All-Series kernel: [605905.272833] usb 2-6: USB disconnect, device number 7
Nov  9 07:31:11 romeo-All-Series kernel: [605905.273291] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
Nov  9 07:31:11 romeo-All-Series kernel: [605905.273334] pl2303 2-6:1.0: device disconnected

```
And after

```
# tail -f /var/log/syslog
....
Nov  9 07:31:53 romeo-All-Series kernel: [605947.816765] usb 2-6: new full-speed USB device number 8 using xhci_hcd
Nov  9 07:31:53 romeo-All-Series kernel: [605947.969345] usb 2-6: New USB device found, idVendor=067b, idProduct=2303
Nov  9 07:31:53 romeo-All-Series kernel: [605947.969353] usb 2-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov  9 07:31:53 romeo-All-Series kernel: [605947.969358] usb 2-6: Product: USB-Serial Controller D
Nov  9 07:31:53 romeo-All-Series kernel: [605947.969362] usb 2-6: Manufacturer: Prolific Technology Inc. 
Nov  9 07:31:53 romeo-All-Series kernel: [605947.969969] pl2303 2-6:1.0: pl2303 converter detected
Nov  9 07:31:53 romeo-All-Series kernel: [605947.970699] usb 2-6: pl2303 converter now attached to ttyUSB0
Nov  9 07:31:53 romeo-All-Series mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-6"
Nov  9 07:31:53 romeo-All-Series mtp-probe: bus: 2, device: 8 was not an MTP device

missing:

gpsd.hotplug: gpsd_control(action=add, arg=/dev/ttyUSB0)
gpsd.hotplug: launching gpsd  -F /var/run/gpsd.sock

# gpsd -N -n -F /var/run/gpsd.sock -D 5
gpsd:PROG: control socket opened at /var/run/gpsd.sock
gpsd:INFO: launching (Version 3.15)
gpsd:IO: opening IPv4 socket
gpsd:IO: opening IPv6 socket
gpsd:INFO: listening on port gpsd
gpsd:PROG: NTP: shmat(195002428,0,0) succeeded, segment 0
gpsd:PROG: NTP: shmat(195035197,0,0) succeeded, segment 1
gpsd:PROG: NTP: shmat(195067966,0,0) succeeded, segment 2
gpsd:PROG: NTP: shmat(195100735,0,0) succeeded, segment 3
gpsd:PROG: NTP: shmat(195133504,0,0) succeeded, segment 4
gpsd:PROG: NTP: shmat(195166273,0,0) succeeded, segment 5
gpsd:PROG: NTP: shmat(195199042,0,0) succeeded, segment 6
gpsd:PROG: NTP: shmat(195231811,0,0) succeeded, segment 7
gpsd:PROG: successfully connected to the DBUS system bus
gpsd:PROG: shmget(0x47505344, 8936, 0666) for SHM export succeeded
gpsd:PROG: shmat() for SHM export succeeded, segment 195264580
gpsd:INFO: running with effective group ID 20
gpsd:INFO: running with effective user ID 124
gpsd:INFO: startup at 2018-11-09T05:51:20.000Z (1541742680)
```

it is above me

```
#gpsmon

gpsmode screen

tcp://localhost:2947          JSON slave driver>
(90) {"class":"VERSION","release":"3.15","rev":"3.15-2build1","proto_major":3,"proto_minor":11}
(32) {"class":"DEVICES","devices":[]}
(122) {"class":"WATCH","enable":true,"json":false,"nmea":false,"raw":2,"scaled":false,"timing":false,"split24":false,"pps":tr
ue}

```
no data, wait for 5 min, and,

```
# gpsd -N -n -F /var/run/gpsd.sock -D 5
gpsd:PROG: control socket opened at /var/run/gpsd.sock
gpsd:INFO: launching (Version 3.15)
gpsd:IO: opening IPv4 socket
gpsd:IO: opening IPv6 socket
gpsd:INFO: listening on port gpsd
gpsd:PROG: NTP: shmat(195002428,0,0) succeeded, segment 0
gpsd:PROG: NTP: shmat(195035197,0,0) succeeded, segment 1
gpsd:PROG: NTP: shmat(195067966,0,0) succeeded, segment 2
gpsd:PROG: NTP: shmat(195100735,0,0) succeeded, segment 3
gpsd:PROG: NTP: shmat(195133504,0,0) succeeded, segment 4
gpsd:PROG: NTP: shmat(195166273,0,0) succeeded, segment 5
gpsd:PROG: NTP: shmat(195199042,0,0) succeeded, segment 6
gpsd:PROG: NTP: shmat(195231811,0,0) succeeded, segment 7
gpsd:PROG: successfully connected to the DBUS system bus
gpsd:PROG: shmget(0x47505344, 8936, 0666) for SHM export succeeded
gpsd:PROG: shmat() for SHM export succeeded, segment 195264580
gpsd:INFO: running with effective group ID 20
gpsd:INFO: running with effective user ID 124
gpsd:INFO: startup at 2018-11-09T05:51:20.000Z (1541742680)
gpsd:CLIENT: => client(0): {"class":"VERSION","release":"3.15","rev":"3.15-2build1","proto_major":3,"proto_minor":11}\x0d\x0a
gpsd:PROG: checking client(0)
gpsd:CLIENT: <= client(0): ?WATCH={"raw":2,"pps":true}\x0d\x0a
gpsd:CLIENT: => client(0): 
{"class":"DEVICES","devices":[]}\x0d\x0a{"class":"WATCH","enable":true,"json":false,"nmea":false,"raw":2,"scaled":false,"timing":false,"split24":false,"pps":true}\x0d\x0a

i stopped gpsmon

# gpsd -N -n -F /var/run/gpsd.sock -D 5
.....
gpsd:PROG: checking client(0)
gpsd:INFO: detaching 127.0.0.1 (sub 0, fd 7) in detach_client
gpsd:CLIENT: => client(0): {"class":"VERSION","release":"3.15","rev":"3.15-2build1","proto_major":3,"proto_minor":11}\x0d\x0a
gpsd:PROG: checking client(0)
gpsd:CLIENT: <= client(0): ?WATCH={"enable":true,"json":true};\x0a
gpsd:CLIENT: => client(0): 
{"class":"DEVICES","devices":[]}\x0d\x0a{"class":"WATCH","enable":true,"json":true,"nmea":false,"raw":0,"scaled":false,"timing":false,"split24":false,"pps":false}\x0d\x0a
gpsd:PROG: checking client(0)
gpsd:INFO: detaching 127.0.0.1 (sub 0, fd 7) in detach_client

$ cgps
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;    Time:       n/a                        &#9474;&#9474;PRN:   Elev:  Azim:  SNR:  Used: &#9474;
&#9474;    Latitude:   n/a                        &#9474;&#9474;                                 &#9474;
&#9474;    Longitude:  n/a                        &#9474;&#9474;                                 &#9474;
&#9474;    Altitude:   n/a                        &#9474;&#9474;                                 &#9474;
&#9474;    Speed:      n/a                        &#9474;&#9474;                                 &#9474;
&#9474;    Heading:    n/a                        &#9474;&#9474;                                 &#9474;
&#9474;    Climb:      n/a                        &#9474;&#9474;                                 &#9474;
&#9474;    Status:     NO FIX (0 secs)            &#9474;&#9474;                                 &#9474;
&#9474;    Longitude Err:   n/a                   &#9474;&#9474;                                 &#9474;
&#9474;    Latitude Err:    n/a                   &#9474;&#9474;                                 &#9474;
&#9474;    Altitude Err:    n/a                   &#9474;&#9474;                                 &#9474;
&#9474;    Course Err:      n/a                   &#9474;&#9474;                                 &#9474;
&#9474;    Speed Err:       n/a                   &#9474;&#9474;                                 &#9474;
&#9474;    Time offset:     n/a                   &#9474;&#9474;                                 &#9474;
&#9474;    Grid Square:     n/a                   &#9474;&#9474;                                 &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
isis    124     ISIS            # IS-IS over IPv4
sctp    132     SCTP            # Stream Control Transmission Protocol
fc      133     FC              # Fibre Channel
mobility-header 135 Mobility-Header # Mobility Support for IPv6 [RFC3775]
udplite 136     UDPLite         # UDP-Lite [RFC3828]
mpls-in-ip 137  MPLS-in-IP      # MPLS-in-IP [RFC4023]
manet   138                     # MANET Protocols [RFC5498]
hip     139     HIP             # Host Identity Protocol
shim6   140     Shim6           # Shim6 Protocol [RFC5533]
wesp    141     WESP            # Wrapped Encapsulating Security Payload
rohc    142     ROHC            # Robust Header Compression
{"class":"WATCH","enable":true,"json":true,"nmea":false,"raw":0,"scaled":false,"timing":false,"split24":false,"pps":false}



# gpsd -V -N
gpsd: 3.15 (revision 3.15-2build1)

# gpsd -l -N | grep SiRF
n       b               *       SiRF


```

Thanks !

---

### Post by ajgreeny on 2018-11-09
You will see I have added code tags (see my signature below for a "how-to") to make the terminal output clearer; please use code tags in future.

I suspect, unfortunately that your problem with the satellite navigation device will not be solvable using Linux; I have yet to find such a device that works with or can be updated using a Linux OS.
To see mine, a TomTom Start 25, I have to use Windows as a VM in VirtualBox.

Do you have information that suggests it should be possible to use Linux to manage that device?

---

### Post by moromete on 2018-11-09
> **ajgreeny said:**
> You will see I have added code tags (see my signature below for a "how-to") to make the terminal output clearer; please use code tags in future.

I suspect, unfortunately that your problem with the satellite navigation device will not be solvable using Linux; I have yet to find such a device that works with or can be updated using a Linux OS.
To see mine, a TomTom Start 25, I have to use Windows as a VM in VirtualBox.

Do you have information that suggests it should be possible to use Linux to manage that device?

No, is not the gps usb.
# systemctl start gpsd
# systemctl status gpsd
&#9679; gpsd.service - GPS (Global Positioning System) Daemon
   Loaded: loaded (/lib/systemd/system/gpsd.service; disabled; vendor preset: enabled)
   Active: active (running) since Vi 2018-11-09 12:17:41 EET; 6s ago
 Main PID: 20640 (gpsd)
   CGroup: /system.slice/gpsd.service
           &#9492;&#9472;20640 /usr/sbin/gpsd -N ----------- this is the problem, '-N' terminate

and udev not working corectly.

#systemctl stop gpsd
#systemctl stop gpsd.socket

and now, after inserting USB GPS, in terminal:

#gpsd -n /dev/ttyUSB0 

'-n' don't wait standby for usb gps.

in another console, all working now gpsmon, cgps, xgps, ...

the real problem is udev

---

