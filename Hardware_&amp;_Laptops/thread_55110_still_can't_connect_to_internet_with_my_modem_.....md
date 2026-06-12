---
title: "still can't connect to internet with my modem ...... HELP"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by HasH on 2005-08-07
i've tried in both 2.6.10-5-386 & 2.6.10-5-686 ,but got the same problem
i do believe that i have the driver correctly installed
here ist the result of lspci :


> 0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 0 3)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03 )
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Contr oller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 01)
[COLOR=DarkOliveGreen]**0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem  Controller (rev 01)**[/COLOR]
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controlle r (rev 01)
0000:02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controlle r (rev 01)
0000:02:01.0 Ethernet controller: Intel Corp. 82540EP Gigabit Ethernet Controlle r (Mobile) (rev 03)
0000:02:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)


and wvdial can also find my modem :

> Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47  S48
Port Scan<*1>: S49  S50  S51  S52  S53
ttySL0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"


my wvdial.conf :


> [Dialer Defaults]
Modem = /dev/ttySL0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = ATH1
Init4 = AT+GCI=42
Stupid Mode = yes
Carrier Check = 0
Modem Type = Analog Modem
Phone = 01920786
Username = arcor
Password = internet



but when i wvdial :


> --> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: ATH1
ATH1
OK
--> Sending: AT+GCI=42
AT+GCI=42
OK
--> Modem initialized.
--> Sending: ATDT01920786
--> Waiting for carrier.
ATDT01920786
NO DIALTONE
--> No dial tone.
--> Disconnecting at Sun Aug  7 20:35:40 2005



so please, tell me what can i do..... i'v already spend a week to drive my modem ......

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 on your system do have on-board LAN
if so it maybe worth while getting an ethernet modem (no drivers required)
it works on both windows & linux
and will be one of the best investments you will make

there are single port multi user ethernet modems available for about £25

this was my way forward when i installed linux, all else seemed to fail ...

---

### Post by HasH on 2005-08-07
[QUOTE=Gezzer]on your system do have on-board LAN
if so it maybe worth while getting an ethernet modem (no drivers required)
it works on both windows & linux
and will be one of the best investments you will make

there are single port multi user ethernet modems available for about £25

this was my way forward when i installed linux, all else seemed to fail ...[/QUOTE]
 Thanks !
but if possible ,i'd rather not to buy a new hardware......

---

### Post by ry_ry on 2005-08-07
I'm still very much a newb, but you might want to edit your wvdial.conf file, and change the "Check carrier = 0" to "Check carrier = no" and see if that works. I'm guessing you have your telephone line connected to the back of your modem too.

---

### Post by Savage790 on 2005-08-08
Your modem is set to wait dial tone before dialing. Find out where you can disable it and do it. Or you just add the (I think it was) X3 to the init string. Try it it helped for me.

---

