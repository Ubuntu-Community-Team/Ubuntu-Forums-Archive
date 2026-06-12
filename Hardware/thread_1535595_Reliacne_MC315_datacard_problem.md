---
title: "Reliacne MC315 datacard problem"
date: 2010-07-21
forum: Hardware
---

### Post by jyotirmoyr on 2010-07-21
I have installed wvdial and setserial. The baud_base is set to 460800. 
The wvdial.conf setting is 

[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 57600
SetVolume = 0
Dial-AT-OK ATDT Command =
Init1 = ATZ
FlowControl = Hardware (CRTSCTS)
Phone = #777
Username = 93737#####
Password = 937374####
New PPPD = yes
Carrier Check = no
Stupid Mode = 1

when I am changing uart to 16550A,16750,16850,16950 and doing sudo wvdial. The ouotput is

jyotirmoyr@U-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
jyotirmoyr@U-laptop:~$ clear

jyotirmoyr@U-laptop:~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
jyotirmoyr@U-laptop:~$ 

Its getting connected once in say 50 tries. Please help

---

