---
title: "Please help. N96 does not connect"
date: 2009-09-12
forum: Hardware
---

### Post by Nole1 on 2009-09-12
Please somebody help. N96 will not connect to internet. Here is the sample of trying to get the connection. Previous phone Nokia 3110C was working perfectly using this wvdial.conf file. I need the connection badly because here in Sahara this is the only way to communicate.
root@novica-laptop:/home/novica# gedit /etc/wvdial.conf
root@novica-laptop:/home/novica# lsusb
Bus 002 Device 006: ID 0421:003a Nokia Mobile Phones 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 004: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@novica-laptop:/home/novica# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Sep 11 12:56:51 2009
--> Pid of pppd: 5352
--> Using interface ppp0
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> Disconnecting at Fri Sep 11 12:56:55 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Sep 11 12:57:04 2009
--> Pid of pppd: 5372
--> Using interface ppp0
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> Disconnecting at Fri Sep 11 12:57:08 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 10 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Sep 11 12:57:21 2009
--> Pid of pppd: 5381
--> Using interface ppp0
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> pppd: ï¿½[7f]
--> Disconnecting at Fri Sep 11 12:57:25 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 20 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
^CCaught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Fri Sep 11 12:57:30 2009
root@novica-laptop:/home/novica# gedit /etc/wvdial.conf
root@novica-laptop:/home/novica# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Sep 11 12:57:58 2009
--> Pid of pppd: 5396
--> Using interface ppp0
--> pppd: [02][7f]
--> pppd: [02][7f]
--> pppd: [02][7f]
--> pppd: [02][7f]
--> pppd: [02][7f]
--> pppd: [02][7f]
--> Disconnecting at Fri Sep 11 12:58:02 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Sep 11 12:58:11 2009
--> Pid of pppd: 5405
--> Using interface ppp0
--> pppd: [02][7f]
--> pppd: [02][7f]
--> pppd: [02][7f]
--> pppd: [02][7f]
--> pppd: [02][7f]
--> pppd: [02][7f]
--> Disconnecting at Fri Sep 11 12:58:15 2009
^CCaught signal 2:  Attempting to exit gracefully...
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 10 seconds
--> Disconnecting at Fri Sep 11 12:58:17 2009

---

