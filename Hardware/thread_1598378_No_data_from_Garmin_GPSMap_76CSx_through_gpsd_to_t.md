---
title: "No data from Garmin GPSMap 76CSx through gpsd to tango GPS"
date: 2010-10-16
forum: Hardware
---

### Post by petersfreeman on 2010-10-16
**Summary**

I have a GPS unit that I am trying to get working with gpsd and tangoGPS.  I have tried many things listed in other forum posts so far with no success.  I need to have a comprehensive step-by-step testing process to determine that each step of the communication process between the GPS unit and tangoGPS is working.

**Environment**

Ubuntu 10.10 Maverick Meerkat i386
Linux 2.6.35-22-generic-pae
GNOME 2.32.0
Memory 4GB

Garmin GPSMap 76CSx
Interface set to NMEA In and NMEA Out
Baud Rate 4800

tangoGPS 0.99.3

**Process**

[LIST=1]
[*]Boot Computer
[*]Plug in USB cable
[*]Connect GPS unit
[*]Turn on GPS unit
[*]When satellites have been acquired, start tangoGPS
[/LIST]

**Configuration**

```
peter@Laptop:~$ sudo dpkg-reconfigure gpsd
```

Question and responses:

```
If you accept this option, gpsd will be started automatically
Start gpsd automatically? **YES**

As gpsd only handles GPS devices, it is safe to choose this option.
However, you can disable it if gpsd is causing interference with
other attached devices or programs. Should gpsd handle attached USB
GPS receivers automatically?  **YES**

Please enter the device the GPS receiver is attached to. It will
probably be something like /dev/ttyS0 or /dev/ttyUSB0.
Multiple devices may be specified as a space-separated list. Leave
empty if you don't want to connect gpsd to a device on boot or if
you want to use device autodetection only.
Device the GPS receiver is attached to:  **/dev/ttyUSB0**

You can give additional arguments when starting gpsd; see gpsd(8)
for a list of options. 
Do not use '-F' here. The control socket path is set independently.
Options to gpsd: **<no options listed>**

Please enter the gpsd control socket location. Usually you want to
keep the default setting. 
gpsd control socket path: **/var/run/gpsd.sock**
```

**Tests**

When tangoGPS Loads, two messages in status area at bottom of window:
[LIST]
[*]No GPS
[*]No GPSD
[/LIST]

```
peter@Laptop:~$ gpscat -s 4800N1
Traceback (most recent call last):
  File "/usr/bin/gpscat", line 66, in <module>
    tty = os.open(arguments[0], os.O_RDWR)
IndexError: list index out of range
```

```
peter@Laptop:~$ lsmod | grep 'usb'
usbhid                 36978  0 
hid                    67742  1 usbhid
```

```
peter@Laptop:~$ gpspipe -w -n 100
netlib_connectsock() returns socket on fd 3
{"class":"VERSION","release":"2.94","rev":"2010-05-13T11:53:05","proto_major":3,"proto_minor":2}
{"class":"DEVICES","devices":[{"class":"DEVICE","path":"/dev/ttyUSB0"}]}
{"class":"WATCH","enable":true,"json":true,"nmea":false,"raw":0,"scaled":false,"timing":false}
```

```
peter@Laptop:~$ ps -C gpsd -fww
UID        PID  PPID  C STIME TTY          TIME CMD
nobody    1320     1  0 09:48 ?        00:00:00 /usr/sbin/gpsd -F /var/run/gpsd.sock -P /var/run/gpsd.pid /dev/ttyUSB0

```

```
peter@Laptop:~$ sudo kill 1320
peter@Laptop:~$ gpsd -N -n -D 2 /dev/ttyUSB0
gpsd: launching (Version 2.94)
gpsd: listening on port gpsd
gpsd: running with effective group ID 1000
gpsd: running with effective user ID 1000
gpsd: opening read-only GPS data source type 0 and at '/dev/ttyUSB0'
gpsd: device open failed: No such file or directory - retrying read-only
gpsd: read-only device open failed: No such file or directory
gpsd: GPS device /dev/ttyUSB0 nonexistent or can't be read
gpsd: opening read-only GPS data source type 0 and at '/dev/ttyUSB0'
gpsd: device open failed: No such file or directory - retrying read-only
gpsd: read-only device open failed: No such file or directory
gpsd: client(0): device activation failed.

```

```
peter@Laptop:~$ gpsprof -f cycle
gpsprof: gpsd unreachable.

```

```
peter@Laptop:~$ ls -la /dev/ttyU*
ls: cannot access /dev/ttyU*: No such file or directory
```

```
peter@Laptop:~$ ls -la /dev/u*
crw-r----- 1 root root  10, 223 2010-10-16 07:45 /dev/uinput
crw-rw-rw- 1 root root   1,   9 2010-10-16 07:45 /dev/urandom
crw-rw---- 1 root root 252,   0 2010-10-16 07:45 /dev/usbmon0
crw------- 1 root root 252,   1 2010-10-16 07:45 /dev/usbmon1
crw------- 1 root root 252,   2 2010-10-16 07:45 /dev/usbmon2
crw------- 1 root root 252,   3 2010-10-16 07:45 /dev/usbmon3
crw------- 1 root root 252,   4 2010-10-16 07:45 /dev/usbmon4
crw------- 1 root root 252,   5 2010-10-16 07:45 /dev/usbmon5
crw------- 1 root root 252,   6 2010-10-16 07:45 /dev/usbmon6
crw------- 1 root root 252,   7 2010-10-16 07:45 /dev/usbmon7
crw------- 1 root root 252,   8 2010-10-16 07:45 /dev/usbmon8
```


**Conclusion**

It seems to me that there is no ttyUSB0 device.
[LIST=1]
[*]Do I have to create ttyUSB0?
[*]Should I use another usb device?
[*]Which device should I use?
[/LIST]

**Request**

Can you tell me:
[LIST=1]
[*]How can I determine which USB port is being used when I plug in the GPS unit?
[*]How do I tell if the USB port is being recognised by gpsd?
[*]How do I tell if the correct baud rate is being used by gpsd
[*]How do I test that gpsd is sending data to tangoGPS
[*]Should I start the GPS unit before starting tangoGPS or the other way around 
[/LIST] 

Finally, what steps should I take to get everything working?

Thank you,

Peter Freeman

---

### Post by petersfreeman on 2010-10-16
Some more testing:

```
peter@Laptop:~$ dmesg
[14397.792199] usb 5-1: new full speed USB device using uhci_hcd and address 3
```

I'm not sure what actual device it is using.

Peter

---

### Post by petersfreeman on 2010-10-16
Some more testing:

```
peter@Laptop:~$ dmesg
[14397.792199] usb 5-1: new full speed USB device using uhci_hcd and address 3
```

I then disconnected it and reconnected it again

```
peter@Laptop:~$ sudo tail -f /var/log/messages
Oct 16 14:38:11 Laptop kernel: [17417.920228] usb 5-1: new full speed USB device using uhci_hcd and address 4

```

The address has changed from 3 to 4

```
peter@Laptop:~$ nc localhost 2947
peter@Laptop:~$

```
(Nothing returned)

```
peter@Laptop:~$ xgps

```
the xgps GUI loads with no data in the fields.  In the line just below the map and satellite information is:

```
{"class":"VERSION","release":"2.94","rev":"2010-05-13T11:53:05","proto_major":3,"proto_minor":2}

```
I'm not sure what actual device it is using.  It seems to me that I need to figure out the correct device to at least connect tangoGPS with gpsd

Peter

---

### Post by petersfreeman on 2010-10-17
I borrowed a USB GPS Receiver from my neighbour.  It is a simple puck device (I think it is referred to as a "mouse").  I don't know what brand it is as it just has on the bottom:  

"GPS Receiver Model: GM12 Output: USB; Length 3 Metres"

The 3 metres refers to the USB cable length

I unplugged my Garmin GPSMap 76CSx and plugged the GM12 in instead and everything worked fine.  It created a /dev/ttyUSB0 device file, I loaded tangoGPS and it located me correctly.  I walked around the neighbourhood and it tracked my motion just as it should.  

When I initially plugged in the GM12, These were the associated lines of dmesg

```
Oct 16 20:05:09 Laptop kernel: [15368.484188] usb 6-2: new full speed USB device using uhci_hcd and address 5
Oct 16 20:05:09 Laptop kernel: [15368.687643] usbcore: registered new interface driver usbserial
Oct 16 20:05:09 Laptop kernel: [15368.687666] USB Serial support registered for generic
Oct 16 20:05:09 Laptop kernel: [15368.687698] usbcore: registered new interface driver usbserial_generic
Oct 16 20:05:09 Laptop kernel: [15368.687700] usbserial: USB Serial Driver core
Oct 16 20:05:09 Laptop kernel: [15368.702678] USB Serial support registered for pl2303
Oct 16 20:05:09 Laptop kernel: [15368.703530] pl2303 6-2:1.0: pl2303 converter detected
Oct 16 20:05:09 Laptop kernel: [15368.714824] usb 6-2: pl2303 converter now attached to ttyUSB0
Oct 16 20:05:09 Laptop kernel: [15368.714847] usbcore: registered new interface driver pl2303
Oct 16 20:05:09 Laptop kernel: [15368.714850] pl2303: Prolific PL2303 USB to serial adaptor driver
```

When I plug in the Garmin GPSMAP76CSx, I only get one line in the log files:

```
Oct 16 23:09:30 Laptop kernel: [10488.328076] usb 6-2: new full speed USB device using uhci_hcd and address 5
```

It seems that the Garmin GPSMAP76CSx does not  stimulate usbcore to register it as a usbserial interface driver.

So now the questions I have are:

[LIST=1]
[*]Can I get my Garmin GPSMAP76CSx using its USB cable to function as the G12 did?
[*]Has anyone managed to get Garmin GPSMAP 76 handhelds to work using the USB cable?
[*]Do I have to purchase the special serial cable that plugs into the back of the GPS Unit, then go through a Serial to USB converter to make it work?
[/LIST] 

Using the four pronged serial interface has been tested as shown at this link:  [http://gpsd.berlios.de/hardware.html]("http://gpsd.berlios.de/hardware.html")

Thank you for your help,

Peter Freeman

---

### Post by petersfreeman on 2010-10-18
I have it all working now.  I am writing up the solution at:

[https://help.ubuntu.com/community/GarminGPSMap76CSx]("https://help.ubuntu.com/community/GarminGPSMap76CSx")

Peter

---

### Post by handaxe on 2010-10-25
Thanks for the write-up (and your persistence:) )

---

