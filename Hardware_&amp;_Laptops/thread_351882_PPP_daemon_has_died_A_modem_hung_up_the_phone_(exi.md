---
title: "PPP daemon has died: A modem hung up the phone (exit code = 16)"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by HilliBilly on 2007-02-02
hi,

need your help. **why has the ppp daemon died?**

(using a motorola razr v3 mobile phone, connected via usb cable to my sharp pc-um10 laptop with edgy gnome.)


XYZ@XYZ-ubuntu-laptop:~$ **sudo wvdial mobile**
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Feb  2 21:06:49 2007
--> Pid of pppd: 20738
--> Using interface ppp0
--> pppd: 8[01][06][08]X[03][06][08]
--> pppd: 8[01][06][08]X[03][06][08]
--> pppd: 8[01][06][08]X[03][06][08]
--> pppd: 8[01][06][08]X[03][06][08]
--> pppd: 8[01][06][08]X[03][06][08]
--> pppd: 8[01][06][08]X[03][06][08]
--> Disconnecting at Fri Feb  2 21:06:51 2007
**--> The PPP daemon has died: A modem hung up the phone (exit code = 16)**
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds


XYZ@XYZ-ubuntu-laptop:/etc$ **sudo gedit /etc/wvdial.conf **
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3 
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 1234567890
Modem = /dev/ttySL0
Username = abcde
Password = abcde
Baud = 115200
Carrier Check = no
#Stupid mode = yes

[Dialer mobile] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 57600 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = *99***1# 
Username = orange
Password = orange
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh]
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP


XYZ@XYZ-ubuntu-laptop:~$ **tail -f /var/log/messages**
Feb  2 21:07:08 XYZ-ubuntu-laptop pppd[20770]: pppd 2.4.4 started by root, uid 0
Feb  2 21:07:08 XYZ-ubuntu-laptop pppd[20770]: Using interface ppp0
Feb  2 21:07:08 XYZ-ubuntu-laptop pppd[20770]: Connect: ppp0 <--> /dev/ttyACM0
Feb  2 21:07:08 XYZ-ubuntu-laptop pppd[20770]: PAP authentication succeeded
Feb  2 21:07:09 XYZ-ubuntu-laptop pppd[20770]: LCP terminated by peer (^E^@^@^J^@^@^@^@^@^@)
Feb  2 21:07:09 XYZ-ubuntu-laptop pppd[20770]: Modem hangup
Feb  2 21:07:09 XYZ-ubuntu-laptop pppd[20770]: Connection terminated.
Feb  2 21:07:09 XYZ-ubuntu-laptop pppd[20770]: Exit.


XYZ@XYZ-ubuntu-laptop:~$ **vi /etc/ppp/peers/wvdial**
noauth
name wvdial
usepeerdns
lcp-echo-failure 0
lcp-echo-interval 0


XYZ@XYZ-ubuntu-laptop:~$ **sudo cat /proc/bus/usb/devices **
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:07.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=02(comm.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  2
P:  Vendor=22b8 ProdID=4902 Rev= 0.01
S:  Manufacturer=Motorola Inc.
S:  Product=Motorola Phone (V3)
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=cdc_acm
E:  Ad=89(I) Atr=03(Int.) MxPS=  16 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
E:  Ad=01(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
C:  #Ifs= 2 Cfg#= 2 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=
E:  Ad=89(I) Atr=03(Int.) MxPS=  16 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=
E:  Ad=01(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms



(was using this HOWTO: [http://www.ubuntuforums.org/showthread.php?t=343989&highlight=evdo](http://www.ubuntuforums.org/showthread.php?t=343989&highlight=evdo))

---

### Post by HilliBilly on 2007-02-02
solved it  :) 


[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3 
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 1234567890
Modem = /dev/ttySL0
Username = abcdefgh
Password = abcdefgh
Baud = 115200
Carrier Check = no
#Stupid mode = yes

[Dialer GPRS] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 57600
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
#INIT5 = AT+CGDCONT=1,"IP","internet"
**INIT5 = AT+CGDCONT=1,"IP","[COLOR="Red"]orange.fr[/COLOR]"**
Phone = *99***1#
#Phone= *99# 
Username = internet
Password = orange
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh]
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP


[Dialer GSM] 
Stupid Mode = on 
Modem = /dev/ttyACM0 
Baud = 14400 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Phone = 1234567890
Username = absdefgh
Password = abcdefgh
Init1 = ATZ 
ISDN = 0 
Modem Type = Analog Modem 
Auto Reconnect = on 
Carrier Check = no 
[Dialer shh]
Init3 = ATM0 
[Dialer pulse] 
Dial Command = ATDP

---

### Post by magichsjx on 2007-02-14
I suggest you uncomment(remove #) from where it says stupid mode =on for starters.in your wvdial.conf file. make sure you are pointing to the port where your modem is by using
> sudo wvdialconf which should point out where the modem link is pointing to. Use this instead of /dev/modem and you should be able to connect again. You can also try to setup modem using pppconfig as root and use pon, poff, and plog to connect, disconnect, or see the connection status. Hope this helps.

---

### Post by eyecolor on 2008-01-17
thnxx
after long searching found your solution...
that works for my sony ericsson k550i

:guitar:

---

### Post by Luca1963 on 2008-07-08
Hi, can you please tell me what did you write in your wvdial.conf ? I have a Sony Ericsson V640i but I can't manage to connect to Internet.
Thanks
Regards.
Luca

[email]l.redaelli@tiscali.it[/email]

---

