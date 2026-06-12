---
title: "Network UPS Tool (NUT) stopped working in 11.04 Natty"
date: 2011-05-05
forum: Hardware
---

### Post by neptune on 2011-05-05
Hi,

NUT was working prior to upgrade but now get the errors below.
My UPS is connected via USB.

I suspect maybe a permissions issue somewhere?? Looking for assistance.. greatly appreciated!

Thanks

```

$ sudo upsdrvctl start
Network UPS Tools - UPS driver controller 2.6.0
Network UPS Tools - Generic HID driver 0.35 (2.6.0)
USB communication driver 0.31
Using subdriver: CyberPower HID 0.3
libusb_get_report: error sending control message: Operation not permitted
Can't initialize data from HID UPS
Driver failed to start (exit status=1)
```

```

$ sudo /etc/init.d/nut start
 * Starting Network UPS Tools                                            [ OK ] 
                                                                               
Broadcast Message from nutmon@forester                                         
        (somewhere) at 13:30 ...                                               
                                                                               
Communications with UPS GS-UPS@localhost lost                                  
                                                                               
                                                                               
Broadcast Message from nutmon@forester                                         
        (somewhere) at 13:30 ...                                               
                                                                               
UPS GS-UPS@localhost is unavailable                                            
```




My config files are as follows:

ups.conf
```

[GS-UPS]
driver = usbhid-ups
port = auto
desc = "Geek Squad UPS"
```

upsd.conf
```

LISTEN 127.0.0.1
LISTEN 192.168.1.20
```

upsd.users
```

[ups-master]
password = pass
actions = SET
instcmds = ALL
upsmon master 

[ups-user]
password = pass
upsmon slave 
```

upsmon.conf
```

MONITOR GS-UPS@localhost 1 ups-master pass master
SHUTDOWNCMD "/sbin/shutdown -h +0"
RUN_AS_USER nutmon
```

nut.conf
```

MODE=netserver
```

/etc/default/nut
```

START_UPSD=yes
START_UPSMON=yes
```

---

### Post by gnwiii on 2011-05-08
I have the same problem with a similar configuration.  The original configuration used user:group "nut:nut".  There have been a number of
changes in the configuration, so I took the new config files and copied the relevant parts of the old configuration.   I get different errors depending on the "-u" setting:

```

$ id nut
uid=120(nut) gid=130(nut) groups=130(nut),20(dialout)
$ sudo /lib/nut/usbhid-ups -DDDD -a belkin -u root
Network UPS Tools - Generic HID driver 0.35 (2.6.0)
USB communication driver 0.31
   0.000000     debug level is '4'
   0.000718     upsdrv_initups...

   [...]
   0.005718     Device does not match - skipping
   0.005731     Checking device (050D/0980) (002/003)
   0.018030     - VendorID: 050d
   0.018048     - ProductID: 0980
   0.018056     - Manufacturer:        
   0.018063     - Product: UPS
   0.018070     - Serial Number: unknown
   0.018077     - Bus: 002
   0.018083     Trying to match device
   0.018093     Device matches
   0.022979     HID descriptor, method 1: (9 bytes) => 09 21 00 01 21 01 22 34 03
   0.022997     i=0, extra[i]=09, extra[i+1]=21
   0.023010     HID descriptor, method 2: (9 bytes) => 09 21 00 01 21 01 22 34 03
   0.023019     HID descriptor length 820
   0.112448     Report Descriptor size = 820
   [...]
   0.113052     Using subdriver: Belkin HID 0.12
   0.113064     Entering libusb_get_report
   0.115000     libusb_get_report: No error
   0.115041     Can't retrieve Report 01: Inappropriate ioctl for device
   0.115062     Path: UPS.BELKINConfig.BELKINConfigVoltage, Type: 
Feature, ReportID: 0x01, Offset: 0, Size: 8  
   [...]
$ ls -l /dev/bus/usb/002/003
0 crw-rw-r-- 1 root nut 189, 130 2011-05-08 13:08 /dev/bus/usb/002/003

```

Running as non-root the error is "operation not permitted":

```

$ sudo /lib/nut/usbhid-ups -DD -a belkin
[...]
   0.261983     libusb_get_report: error sending control message: Operation not permitted
   0.262002     Can't retrieve Report 29: Operation not permitted

```

---

### Post by neptune on 2011-05-26
still trying to find a solution to my issue.... :(

---

### Post by zivagolee on 2011-06-05
Just upgraded to Natty and i'm getting this issue too :(

---

### Post by maddentim on 2011-06-13
Hello, anyone have any luck resolving? Perhaps this bug report is related to our difficulties: [https://bugs.launchpad.net/ubuntu/+source/nut/+bug/779512](https://bugs.launchpad.net/ubuntu/+source/nut/+bug/779512)

The reporter solved it, but only by building from source which I would prefer to avoid...

---

### Post by samsonite801 on 2012-03-09
.
Aye no, a really old thread yes, but I just had this same issue as well.


I find that if I remove the external IP entries from my upsd.conf LISTEN directive, so there is a single entry for lo IP then it works...

So in other words, when it looks like this:

[B][COLOR="SeaGreen"]LISTEN 127.0.0.1 3493
LISTEN 1.1.1.7 3493
LISTEN 1.1.1.15 3493[/COLOR][/B]

Then the output when starting the service looks like this:

  [B][I]Broadcast Message from nut@myserver
        (somewhere) at 20:27 ...

Communications with UPS usbhid@localhost lost


Broadcast Message from nut@myserver
        (somewhere) at 20:27 ...

UPS usbhid@localhost is unavailable[/I][/B]


and then I get:

me@myserver:~$ sudo upsc usbhid@localhost
Error: Connection failure: Connection refused

--------------------

But if I comment out my external IPs in upsd.conf like this:

 [B][COLOR="SeaGreen"]LISTEN 127.0.0.1 3493[/COLOR]
[COLOR="DeepSkyBlue"]#LISTEN 1.1.1.7 3493
#LISTEN 1.1.1.15 3493[/COLOR][/B]

Then the service starts fast and normal and then I get:


me@myserver:~$ sudo upsc usbhid@localhost
battery.charge: 100
battery.charge.low: 10
battery.charge.warning: 50
battery.date: not set
battery.mfr.date: 2011/11/13
battery.runtime: 4650
battery.runtime.low: 120
battery.type: PbAc
battery.voltage: 13.4
battery.voltage.nominal: 12.0
device.mfr: APC
device.model: Back-UPS ES 725
device.serial: 3B0601X12900
device.type: ups
driver.name: usbhid-ups
driver.parameter.pollfreq: 30
driver.parameter.pollinterval: 2
driver.parameter.port: usb
driver.version: 2.6.1
driver.version.data: APC HID 0.95
driver.version.internal: 0.35
input.sensitivity: high
input.transfer.high: 138
input.transfer.low: 88
input.voltage: 119.0
input.voltage.nominal: 120
ups.beeper.status: disabled
ups.delay.shutdown: 20
ups.firmware: 802.n5.D
ups.firmware.aux: n5
ups.load: 0
ups.mfr: APC
ups.mfr.date: 2005/12/29
ups.model: Back-UPS ES 725
ups.productid: 0002
ups.serial: 3B0601X12900
ups.status: OL
ups.timer.reboot: 0
ups.timer.shutdown: -1
ups.vendorid: 051d

..as should be expected.

My only problem, is I need to be able to listen on the other 2 IPs to my slaves on 3493 but it doesn't work.

Can anyone try what I did and see if they are seeing the same symptom I am seeing?

I might try and see if I can just forward the traffic to lo from my LAN interface in iptables and see if that will work.  Never tried that before but maybe it could fix this?
.
.

---

### Post by jerome fr on 2013-02-23
Hi

quite old post but since i just solved this issue here's the solution:

edit the hosts.allow file and allow your network to access upsd by adding this line:
**upsd : .allowed.domain.name : allow**

i use freeBSD so things can be a bit different on ubuntu but it should work.

bye

---

### Post by codemaniac on 2013-02-23
Old thread closed.

---

