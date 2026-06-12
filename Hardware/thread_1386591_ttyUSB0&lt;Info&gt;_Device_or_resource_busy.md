---
title: "ttyUSB0&lt;Info&gt;: Device or resource busy"
date: 2010-01-20
forum: Hardware
---

### Post by linuxcss on 2010-01-20
I installed an usb actiontec 56k external modem, which I am trying to setup to
use with efax (faxing), however when using that program it always says its waiting
for the device. So I just installed wvdial  ... and I rebooted when
running wvdialconf (below) It also says the device or resource busy.

What adjustments do i need to make??

$ wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

WvModem<*1>: Cannot set information for serial port.
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
ttyUSB0<Info>: Device or resource busy
Modem Port Scan<*1>: USB0 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

---

### Post by GeorgeVita on 2010-01-22
Hi **linuxcss**, try to identify what happens when you attach your modem:

- Boot without modem, **wait** for the system to load
(if you are using USB to RS232 cable or i/f DO NOT attach it)
- do NOT RUN any communication/fax etc. program
- open a terminal window and try: **sudo dmesg -c**
(this will show all system activity till then and will 'clear' this log. Next simple **dmesg** will show only 'new' activity)
- attach modem, power it ON
- **wait** 30-40 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**
- from terminal: **uname -a**

Post output from THE LAST **dmesg** (not from the previous 'sudo dmesg -c') till 'uname -a'.

Regards,
George

---

### Post by linuxcss on 2010-01-25
George,

Here is the output

css@linuxcss0:~$ dmesg
[ 1270.356028] usb 6-1: new full speed USB device using ohci_hcd and address 2
[ 1270.523061] usb 6-1: configuration #1 chosen from 1 choice
[ 1270.588358] usbcore: registered new interface driver usbserial
[ 1270.588384] USB Serial support registered for generic
[ 1270.588441] usbcore: registered new interface driver usbserial_generic
[ 1270.588448] usbserial: USB Serial Driver core
[ 1270.595493] USB Serial support registered for pl2303
[ 1270.595534] pl2303 6-1:1.0: pl2303 converter detected
[ 1270.615774] usb 6-1: pl2303 converter now attached to ttyUSB0
[ 1270.615797] usbcore: registered new interface driver pl2303
[ 1270.615801] pl2303: Prolific PL2303 USB to serial adaptor driver
css@linuxcss0:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:a13c Chicony Electronics Co., Ltd
Bus 001 Device 004: ID 04a9:221c Canon, Inc. CanoScan LiDE 60
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
css@linuxcss0:~$ uname -a
Linux cw200x4-css0 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux
css@linuxcss0:~$

linuxcss

---

### Post by GeorgeVita on 2010-01-25
> **linuxcss said:**
> [ 1270.615774] usb 6-1: pl2303 converter now attached to **ttyUSB0**
[ 1270.615797] usbcore: registered new interface **driver pl2303**
[ 1270.615801] pl2303: Prolific PL2303 USB to serial adaptor driver

Bus 006 Device 002: ID **067b:2303** Prolific Technology, Inc. PL2303 Serial Port

Linux cw200x4-css0 **2.6.31-17**-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux

Hi **linuxcss**, from above data everything seems to be OK regarding your USB to RS232 converter and your updated Ubuntu 9.10

Repeat carefully all steps (just to verify that all data are the same), power ON your modem and issue a new terminal command: ```
screen /dev/ttyUSB0
``` this will begin a serial communication with your modem where you can use AT commands. Type in lower case some commands (the respond will be in UPPER case):
**at** (and press <ENTER> key) the respond must be **OK**
**atz** (and press <ENTER> key) the respond must be **OK**
**at&f** (and press <ENTER> key) the respond must be **OK**
**ati** (and press <ENTER> key), some data will appear
**at&v**  (and press <ENTER> key), more data will appear

Close terminal and reboot to be sure that the port is not 'held' my screen (in case it did not terminated properly).

If your test has similar behaviour as my description, there is no problem with the system/modem/interface and you must check specific fax s/w.

Regards,
George

---

### Post by damiannz on 2010-02-03
we've been having a similar problem. it might be something to do with permissions. 

try starting your app as root (sudo nameoffaxapp).

if that works then it's a permissions issue. note that running as root is not a good option if it's to happen more than once or twice, and you need to fix the underlying permission problem.. i don't know how to do that myself though, so can't help you - sorry!

---

