---
title: "XS Stick P14   klarmobil.de 5000 flat"
date: 2012-09-21
forum: Hardware
---

### Post by KisteBecks on 2012-09-21
had some problems getting this stick to work, this is a ubuntu 12.04 system with current updates.
here are some notes:


[B]short version
[/B]plug in stick
boot
install usb_modeswitch
sudo modprobe usbserial vendor=0x1c9e product=0x9605
create connection as in step 5

**long version**
1. boot
2. install usb_modeswitch #default config
- why do we need this tool?
because the webstick was produced for a windows environment, so after you plug it in it will automatically act as a usb stick and install the needed drivers - works pretty well in windows its just useless for our ubuntu.
usb_modeswitch swiches the device from mass storage to a modem
 
(you may have to restart hal at this point or just reboot the whole system)
after reboot/restart hal:         #somebody can maybe comment on this, to be on the safe side restart the system

3. attach the stick, the stick will start with a longer green blink and then blink red

dmesg says:
```

[  102.455416] usb 2-1.1: new high-speed USB device number 3 using ehci_hcd
[  102.552715] scsi7 : usb-storage 2-1.1:1.0
[  103.552783] scsi 7:0:0:0: CD-ROM            USBModem Disk             2.31 PQ: 0 ANSI: 2
[  103.556954] sr1: scsi-1 drive
[  103.557225] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  103.557381] sr 7:0:0:0: Attached scsi generic sg2 type 5
[  105.952410] usb 2-1.1: USB disconnect, device number 3
[  106.150121] usb 2-1.1: new high-speed USB device number 4 using ehci_hcd
[  106.852942] scsi8 : usb-storage 2-1.1:1.4
[  107.853093] scsi 8:0:0:0: Direct-Access     USBModem Disk             2.31 PQ: 0 ANSI: 2
[  107.853702] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  107.860795] sd 8:0:0:0: [sdb] Attached SCSI removable disk

```4. look at the output from usb_modemswitch.log to see if the stick gets changed from usb mass storage to usb modem, looks like this:
cat /var/log/usb_modeswitch.log 

somewhere at the end it should read:
```

Mode switch succeeded. Bye.

ok:1c9e:9605

```the complete log
```

USB_ModeSwitch log from Fri Sep 21 15:18:39 2012

Using global config file: /etc/usb_modeswitch.conf

Raw args from udev: /2-1.2:1.0

Bus ID for device not given by udev.
 Trying to determine it from kernel name (2-1.2:1.0) ...
Using top device dir /sys/bus/usb/devices/2-1.2

USB dir exists: /sys/bus/usb/devices/2-1.2

SCSI dir exists: /sys/bus/usb/devices/2-1.2
Warning: SCSI attribute "vendor" not readable.
Warning: SCSI attribute "model" not readable.
Warning: SCSI attribute "rev" not readable.
----------------
USB values from sysfs:
  idVendor    1c9e
  idProduct    f000
  manufacturer    USB Modem
  product    USB Modem
  serial    1234567890ABCDEF
  bNumConfigurations    1
----------------
bNumConfigurations is 1 - don't check for active configuration
Found packed config collection /usr/share/usb_modeswitch/configPack.tar.gz
Searching entries named: /usr/share/usb_modeswitch/1c9e:f000*
Searching overriding entries named: /etc/usb_modeswitch.d/1c9e:f000*
SCSI attributes not needed, moving on.

Extracting config 1c9e:f000 from collection /usr/share/usb_modeswitch/configPack.tar.gz
config: TargetVendor set to 1c9e
config: TargetProduct set to 9000,9603,9605,9607
Driver module is "option", ID path is /sys/bus/usb-serial/drivers/option1
! matched, now switching
Command to be run:
/usr/sbin/usb_modeswitch -I -W -D -s 20 -c /run/usb_modeswitch/current_cfg -u -1   -v 1c9e -p f000 2>&1

Verbose debug output of usb_modeswitch and libusb follows
(Note that some USB errors are expected in the process)
--------------------------------

Reading config file: /run/usb_modeswitch/current_cfg
Mode switch succeeded. Bye.

ok:1c9e:9605
 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.2.3 (C) Josua Dietze 2012
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x1c9e
DefaultProduct= 0xf000
TargetVendor=   0x1c9e
TargetProduct=  not set
TargetClass=    not set
TargetProductList="9000,9603,9605,9607"

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
QisdaMode=0
GCTMode=0
KobilMode=0
SequansMode=0
MobileActionMode=0
CiscoMode=0
MessageEndpoint=  not set
MessageContent="55534243123456788000000080000606f50402527000000000000000000000"
NeedResponse=0
ResponseEndpoint= not set

InquireDevice disabled
Success check enabled, max. wait time 20 seconds
System integration mode enabled


Looking for target devices ...
  searching devices, found USB ID 1c9e:f000
   found matching vendor ID
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 058f:a009
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
 No devices in target mode or class found
Looking for default devices ...
  searching devices, found USB ID 1c9e:f000
   found matching vendor ID
   found matching product ID
   adding device
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 058f:a009
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
 Found device in default mode, class or configuration (1)
Accessing device 003 on bus 002 ...
Skipping the check for the current configuration
Using first interface: 0x00
Using endpoints 0x01 (out) and 0x81 (in)

USB description data (for identification)
-------------------------
Manufacturer: USB Modem
     Product: USB Modem
  Serial No.: 1234567890ABCDEF
-------------------------
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached
Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Resetting response endpoint 0x81
Resetting message endpoint 0x01

Checking for mode switch (max. 20 times, once per second) ...
 Searching for target devices ...
  searching devices, found USB ID 1c9e:f000
   found matching vendor ID
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 058f:a009
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
 Searching for target devices ...
  searching devices, found USB ID 1c9e:9605
   found matching vendor ID
   found matching product ID from list
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002
  searching devices, found USB ID 058f:a009
  searching devices, found USB ID 8087:0020
  searching devices, found USB ID 1d6b:0002

Found target device, now opening

Found target device 004 on bus 002

Target device description data
-------------------------
Manufacturer: USB Modem
     Product: USB Modem
  Serial No.: 1234567890ABCDEF
-------------------------
 Found correct target device

Mode switch succeeded. Bye.

ok:1c9e:9605
--------------------------------
(end of usb_modeswitch output)
Checking success of mode switch for max. 20 seconds ... Reading attributes ...
USB dir exists: /sys/bus/usb/devices/2-1.2
 All attributes matched
Mode switching was successful, found 1c9e:9605 (USB Modem: USB Modem)Now checking for bound driver ...
 no driver has bound to interface 0 yet
Device not in "bind_list" yet, bind it now
 modprobe not foundModule loader is (null)
Can't do anymore without module loader; get "modtools"!
 driver binding failed
Checking for AVOID_RESET_QUIRK kernel attribute
 AVOID_RESET_QUIRK activated

All done, exiting

```5. now we need this line:
sudo modprobe usbserial vendor=0x1c9e product=0x9605 #im sry, cant explain why at the moment

run dmesg in a terminal, should show something like this:
```

[   85.742195] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   85.744696] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  482.114272] usbcore: registered new interface driver usbserial
[  482.114291] USB Serial support registered for generic
[  482.114314] usbserial_generic 2-1.2:1.0: generic converter detected
[  482.114477] usb 2-1.2: generic converter now attached to ttyUSB0
[  482.114497] usbserial_generic 2-1.2:1.1: generic converter detected
[  482.114598] usb 2-1.2: generic converter now attached to ttyUSB1
[  482.114615] usbserial_generic 2-1.2:1.2: generic converter detected
[  482.114729] usb 2-1.2: generic converter now attached to ttyUSB2
[  482.114746] usbserial_generic 2-1.2:1.3: generic converter detected
[  482.114846] usb 2-1.2: generic converter now attached to ttyUSB3
[  482.114872] usbcore: registered new interface driver usbserial_generic
[  482.114876] usbserial: USB Serial Driver core

```now modem manager does "something" with the hardware, it does take some minutes...you can follow the progress in /var/log/syslog
if its done a window will pop up and ask you for the PIN


5. 

now you can create a new mobile broadband connection, from the menu:
Network Connections
or from the upper taskbar, click on the network symbol
Edit Connections...

the device is called USB Modem
press continue, choose germany, continue, use "i cant find my provide and enter it manually" - name it klarmobil.de
choose web.vodafone.de as APN
apply


now you can activate the mobile broadband connection from the upper taskbar, this laptop also has settings enabled for eth0 but this was tested without a cable attached.

somewhere in the process of all this the stick starts blinking green, missed the exact point, could be further up.


**AFTER REBOOT**
If you reboot the system you have to redo these steps:
wait until usb-modeswitch switched the device
sudo modprobe usbserial vendor=0x1c9e product=0x9605
wait until you get asked for the pin
connect


if the system goes into suspend (i.e. closing the display on a laptop) 
you have to wait for a few minutes until the klarmobil.de connection will be available again


if this doesnt help feel free to post comments

---

### Post by woidda on 2012-10-02
Fwiw if you have T-Mobil, in step 5 you have to enter:

```

APN: internet.t-mobile
user name: T-Mobile
password: td

```

---

### Post by joooky on 2012-10-10
> **KisteBecks said:**
> had some problems getting this stick to work, this is a ubuntu 12.04 system with current updates.
here are some notes:


[B]short version
[/B]plug in stick
boot
install usb_modeswitch
sudo modprobe usbserial vendor=0x1c9e product=0x9605
create connection as in step 5


Thanks for the great Article. Using your solution I always have to use the modprobe command after I plugged in the stick.

Is it possible to run this command automaticly every time I plug in the stick? How do I do that?

Thanks, jukey

---

### Post by KisteBecks on 2012-12-22
you could add the modprobe command to /etc/rc.local right before the exit 0.
that should work

---

### Post by jkh1234 on 2013-01-23
trying all the steps mentioned above was **not needed to get it working** on  my machine. 

**all i needed to do was** adding the following line to [/etc/modules]("http://wiki.ubuntuusers.de/Kernelmodule#Module-automatisch-laden") to load the correct drivers and than do a reboot:
```
usbserial vendor=0x1c9e product=0x9605
```i guess they implemented all the usb_modeswitch stuff in some update or something like that, trying anything else than loading the correct driver did more harm than good.

---

### Post by KisteBecks on 2013-01-26
i just tested the stick a day ago, the manual way needs to be modified to work now:

```

after boot insert the stick
modprobe usbserial vendor=0x1c9e product=0x9605
usb_modeswitch -c /etc/usb_modeswitch.conf -v 0x1c9e -p 0x9605

```

then the device will become active as you can see in syslog, takes about 30s.
now you can create a connection with the network manager


will test your way tomorrow, thx for the reply.

---

### Post by KisteBecks on 2013-01-26
why cant i edit my original post?

---

