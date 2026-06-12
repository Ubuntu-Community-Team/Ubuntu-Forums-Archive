---
title: "SAMSUNG Galaxy fit as a modem on Ubuntu"
date: 2011-04-21
forum: Hardware
---

### Post by rshinde70 on 2011-04-21
Hello Friends,
I'm using Samsung Galaxy fit smatphone (Android 2.2). I want to use this phone as a modem on my Ubuntu 8.04 LTS. However last time I used my old nokia as a modem with " wvdial " tool to establish ppp connection.

Now, for this new mobile,

wvdialconf gives following output:

rohit@rohit-desktop:~$ sudo wvdialconf
[sudo] password for rohit: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttyACM0<*1>: ATQ0 V1 E1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 Z -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyACM0<*1>: Modem Identifier: ATI -- Manufacturer: SAMSUNG ELECTRONICS CORPORATION
ttyACM0<*1>: Speed 4800: AT -- OK
ttyACM0<*1>: Speed 9600: AT -- OK
ttyACM0<*1>: Speed 19200: AT -- OK
ttyACM0<*1>: Speed 38400: AT -- OK
ttyACM0<*1>: Speed 57600: AT -- OK
ttyACM0<*1>: Speed 115200: AT -- OK
ttyACM0<*1>: Speed 230400: AT -- OK
ttyACM0<*1>: Speed 460800: AT -- OK
ttyACM0<*1>: Max speed is 460800; that should be safe.
ttyACM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found an USB modem on /dev/ttyACM0.
Modem configuration written to /etc/wvdial.conf.
ttyACM0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
rohit@rohit-desktop:~$ 


And the edited wvdial.conf file is as given below:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","rcomnet","",0,0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = *99#
Modem = /dev/ttyACM0
Username = blank
Password = blank
Baud = 460800


In above text, "rcomnet" is the Access Point.

Now, on wvdial create, it gives following output :

rohit@rohit-desktop:~$ sudo wvdial create
--> WvDial: Internet dialer version 1.60
--> Warning: section [Dialer create] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=1,"IP","rcomnet","",0,0
AT+CGDCONT=1,"IP","rcomnet","",0,0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT 57600
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Apr 21 20:05:50 2011
--> Pid of pppd: 2903
--> Using interface ppp0
--> local  IP address 115.246.203.147
--> remote IP address 10.64.64.64
--> primary   DNS address 202.138.117.61
--> secondary DNS address 202.138.96.2

And the problem is that even thought it shows an active connection I can't access the Internet.. :(
Please help me...

---

### Post by a_posse_ad_esse on 2011-04-21
Is there an option to do USB tethering?  I have an Android phone as well and it is in settings->wireless & networks-> USB tethering.

---

### Post by rshinde70 on 2011-04-22
> **a_posse_ad_esse said:**
> Is there an option to do USB tethering?  I have an Android phone as well and it is in settings->wireless & networks-> USB tethering.
I tried tethering but it didn't worked. Phone shows it's connected but no any response in the System.

---

### Post by aysiu on 2011-04-22
I don't think you can use it as a modem that way. If USB tethering doesn't work, you can try rooting the phone and using it as a wireless hotspot.

---

### Post by pythonsyntax on 2011-04-25
I would try the android app call Pdanet it a tethering app work withlinx try thaat and see what happons:)

---

