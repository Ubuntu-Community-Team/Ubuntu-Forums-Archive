---
title: "GUI for UPS?"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by odzx on 2007-03-10
I'm looking for a simple app that can let me configure/control my UPS Uninterruptible power supply . i just bought a partner prpc750 ups by advice. it did come with upsmon that seemed to me as if it was supposed to have a gui to let you control and monitor the ups during a power failure (at least the window version did), but i couldn't find one. 
does anybody know a simple gui that works with this hardware?

---

### Post by odzx on 2007-03-15
bump

---

### Post by ramjet_1953 on 2007-03-16
You may find that this link helps.

[http://sourceforge.net/projects/apcupsd](http://sourceforge.net/projects/apcupsd)

Regards,
Roger :cool:

---

### Post by odzx on 2007-03-16
thanks. i'll try that, though the installation process seems really complicated.

---

### Post by yabbadabbadont on 2007-03-16
```
sudo apt-get install apcupsd
sudo gedit /etc/apcupsd/apcupsd.conf
sudo gedit /etc/default/apcupsd
sudo /etc/init.d/apcupsd start
sudo apcaccess     (just to test it)

```
That's not so hard.  ;)

---

### Post by odzx on 2007-03-17
thanks for that.
it does look  a lot less complicated now. (compared to the instructions on the user manual)
anyway i did that and edited the config file to work with a usb configuration, but when i try to test it i get  this:
> $ sudo apcaccess
FATAL ERROR in apcaccess.c at line 252
tcp_open: cannot connect to server localhost on port 3551.
ERR=Connection timed out
any idea if that is problem?
can i see the status of my ups with out connecting? 
thanks again.

---

### Post by yabbadabbadont on 2007-03-18
I had a typo in one of the lines I posted...  :oops:

You need to edit the /etc/default/apcupsd file and change "ISCONFIGURED=no" to "ISCONFIGURED=yes".  Without doing that, when you ran "sudo /etc/init.d/apcupsd start", it didn't really start up.  That would explain the error you got.

---

### Post by odzx on 2007-03-18
actually i figured that this was a typo, so i already did that, and it did start (before i edited this line it complained that it wasn't configured yet). when i tried to test it i got an error message saying it could not connect through the port. i tried opened the port to make sure it can go through, and then it gave me the error message mentioned above.

---

### Post by yabbadabbadont on 2007-03-18
You shouldn't need to open the port since it is on localhost.  I didn't.  Please post your /etc/apcupsd/apcupsd.conf file, and the make, model, and cable type of your APC UPS.

Edit: include your /etc/hosts file too please.

---

### Post by odzx on 2007-03-18
this is the /etc/hosts file:
> 127.0.0.1	localhost
127.0.1.1	oded-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
my ups is a prpc750 (partner 750vt) manufactured by ADVICE. 
cable type is usb (i assume thats what you mean)
apcupsd.conf :
> ## apcupsd.conf v1.1 ##
# 
#  for apcupsd release 3.12.3 (26 April 2006) - debian
#
# "apcupsd" POSIX config file

#
# ========= General configuration parameters ============
#

# UPSNAME xxx
#   Use this to give your UPS a name in log files and such. This
#   is particulary useful if you have multiple UPSes. This does not
#   set the EEPROM. It should be 8 characters or less.
#UPSNAME

# UPSCABLE <cable>
#   Defines the type of cable connecting the UPS to your computer.
#
#   Possible generic choices for <cable> are:
#     simple, smart, ether, usb
#
#   Or a specific cable model number may be used:
#     940-0119A, 940-0127A, 940-0128A, 940-0020B,
#     940-0020C, 940-0023A, 940-0024B, 940-0024C,
#     940-1524C, 940-0024G, 940-0095A, 940-0095B,
#     940-0095C, M-04-02-2000
#
UPSCABLE usb

# To get apcupsd to work, in addition to defining the cable
# above, you must also define a UPSTYPE, which corresponds to
# the type of UPS you have (see the Description for more details).
# You must also specify a DEVICE, sometimes referred to as a port.
# For USB UPSes, please leave the DEVICE directive blank. For
# other UPS types, you must specify an appropriate port or address.
#
# UPSTYPE   DEVICE           Description
# apcsmart  /dev/tty**       Newer serial character device,
#                            appropriate for SmartUPS models using
#                            a serial cable (not USB).
#
# usb       <BLANK>          Most new UPSes are USB.
#                            A blank DEVICE setting enables
#                            autodetection, which is th best choice
#                            for most installations.
#
# net       hostname:port    Network link to a master apcupsd
#                            through apcupsd's Network Information
#                            Server. This is used if you don't have
#                            a UPS directly connected to your computer.
#
# snmp      hostname:port:vendor:community
#                            SNMP Network link to an SNMP-enabled
#                            UPS device. Vendor is the MIB used by
#                            the UPS device: can be "APC", "APC_NOTRAP"
#                            or "RFC" where APC is the powernet MIB,
#                            "APC_NOTRAP" is powernet with SNMP trap
#                            catching disabled, and RFC is the IETF's 
#                            rfc1628 UPS-MIB. Port is usually 161. 
#                            Community is "private".
#
# dumb      /dev/tty**       Old serial character device for use 
#                            with simple-signaling UPSes.
#
UPSTYPE usb
DEVICE 


# LOCKFILE <path to lockfile>
#   Path for device lock file.
LOCKFILE /var/lock

#
# ======== Configuration parameters used during power failures ==========
#

# The ONBATTERYDELAY is the time in seconds from when a power failure
#   is detected until we react to it with an onbattery event.
#
#   This means that, apccontrol will be called with the powerout argument
#   immediately when a power failure is detected.  However, the
#   onbattery argument is passed to apccontrol only after the 
#   ONBATTERYDELAY time.  If you don't want to be annoyed by short
#   powerfailures, make sure that apccontrol powerout does nothing
#   i.e. comment out the wall.
ONBATTERYDELAY 6

# 
# Note: BATTERYLEVEL, MINUTES, and TIMEOUT work in conjunction, so
# the first that occurs will cause the initation of a shutdown.
#

# If during a power failure, the remaining battery percentage
# (as reported by the UPS) is below or equal to BATTERYLEVEL, 
# apcupsd will initiate a system shutdown.
BATTERYLEVEL 5

# If during a power failure, the remaining runtime in minutes 
# (as calculated internally by the UPS) is below or equal to MINUTES,
# apcupsd, will initiate a system shutdown.
MINUTES 3

# If during a power failure, the UPS has run on batteries for TIMEOUT
# many seconds or longer, apcupsd will initiate a system shutdown.
# A value of 0 disables this timer.
#
#  Note, if you have a Smart UPS, you will most likely want to disable
#    this timer by setting it to zero. That way, you UPS will continue
#    on batteries until either the % charge remaing drops to or below BATTERYLEVEL,
#    or the remaining battery runtime drops to or below MINUTES.  Of course,
#    if you are testing, setting this to 60 causes a quick system shutdown
#    if you pull the power plug.   
#  If you have an older dumb UPS, you will want to set this to less than
#    the time you know you can run on batteries.
TIMEOUT 0

#  Time in seconds between annoying users to signoff prior to
#  system shutdown. 0 disables.
ANNOY 300

# Initial delay after power failure before warning users to get
# off the system.
ANNOYDELAY 60

# The condition which determines when users are prevented from
# logging in during a power failure.
# NOLOGON <string> [ disable | timeout | percent | minutes | always ]
NOLOGON disable

# If KILLDELAY is non-zero, apcupsd will continue running after a
# shutdown has been requested, and after the specified time in
# seconds attempt to kill the power. This is for use on systems
# where apcupsd cannot regain control after a shutdown.
# KILLDELAY <seconds>  0 disables
KILLDELAY 0

#
# ==== Configuration statements for Network Information Server ====
#

# NETSERVER [ on | off ] on enables, off disables the network
#  information server. If netstatus is on, a network information
#  server process will be started for serving the STATUS and
#  EVENT data over the network (used by CGI programs).
NETSERVER on

# NISIP <dotted notation ip address>
#  IP address on which NIS server will listen for incoming connections.
#  Default value is 0.0.0.0 that means any incoming request will be
#  serviced but if you want it to listen to a single subnet you can
#  set it up to that subnet address, for example 192.168.10.0
#  Additionally you can listen for a single IP like 192.168.10.1
NISIP 127.0.0.1

# NISPORT <port> default is 3551 as registered with the IANA
#  port to use for sending STATUS and EVENTS data over the network.
#  It is not used unless NETSERVER is on. If you change this port,
#  you will need to change the corresponding value in the cgi directory
#  and rebuild the cgi programs.
NISPORT 3551

# If you want the last few EVENTS to be available over the network
# by the network information server, you must define an EVENTSFILE.
EVENTSFILE /var/log/apcupsd.events

# EVENTSFILEMAX <kilobytes>
#  By default, the size of the EVENTSFILE will be not be allowed to exceed
#  10 kilobytes.  When the file grows beyond this limit, older EVENTS will
#  be removed from the beginning of the file (first in first out).  The
#  parameter EVENTSFILEMAX can be set to a different kilobyte value, or set
#  to zero to allow the EVENTSFILE to grow without limit.
EVENTSFILEMAX 10

#
# ========== Configuration statements used if sharing =============
#            a UPS and controlling it via the network              

# The configuration statements below are used if you want to share one 
# UPS to power multiple machines and have them communicate by the network.
# Most of these items are for Master/Slave mode only, however NETTIME is
# also used for Client/Server NIS networking with the net driver.

# NETTIME <int>
#   Interval (in seconds) at which the slave or client polls the master
#   or server. This is applicable to BOTH master/slave and client/server
#   (NIS) networking.
#NETTIME 100

#
# Remaining items are for Master/Slave networking ONLY
#

# UPSCLASS [ standalone | shareslave | sharemaster | netslave | netmaster ]
#   Normally standalone unless you share a UPS with multiple machines.
#   
UPSCLASS standalone

# UPSMODE [ disable | share | net | sharenet ]
#   Unless you want to share the UPS (power multiple machines),
#   this should be disable.
UPSMODE disable

# NETPORT <int>
#   Port on which master/slave networking communicates.
#NETPORT 6544

# MASTER <machine-name>
#   IP address of the master. Only applicable on slaves.
#MASTER

# SLAVE <machine-name>
#   IP address(es) of the slave(s). Only applicable on master.
#SLAVE slave1
#SLAVE slave2

# USERMAGIC <string>
#   Magic string use by slaves to identify themselves. Only applicable
#   on slaves.
#USERMAGIC

#
# ===== Configuration statements to control apcupsd system logging ========
#

# Time interval in seconds between writing the STATUS file; 0 disables
STATTIME 0

# Location of STATUS file (written to only if STATTIME is non-zero)
STATFILE /var/log/apcupsd.status

# LOGSTATS [ on | off ] on enables, off disables
# Note! This generates a lot of output, so if         
#       you turn this on, be sure that the
#       file defined in syslog.conf for LOG_NOTICE is a named pipe.
#  You probably do not want this on.
LOGSTATS off

# Time interval in seconds between writing the DATA records to
#   the log file. 0 disables.
DATATIME 0

# FACILITY defines the logging facility (class) for logging to syslog. 
#          If not specified, it defaults to "daemon". This is useful 
#          if you want to separate the data logged by apcupsd from other
#          programs.
#FACILITY DAEMON

#
# ========== Configuration statements used in updating the UPS EPROM =========
#

#
# These statements are used only by apctest when choosing "Set EEPROM with conf
# file values" from the EEPROM menu. THESE STATEMENTS HAVE NO EFFECT ON APCUPSD.
#

# UPS name, max 8 characters 
#UPSNAME UPS_IDEN

# Battery date - 8 characters
#BATTDATE mm/dd/yy

# Sensitivity to line voltage quality (H cause faster transfer to batteries)  
# SENSITIVITY H M L        (default = H)
#SENSITIVITY H

# UPS delay after power return (seconds)
# WAKEUP 000 060 180 300   (default = 0)
#WAKEUP 60

# UPS Grace period after request to power off (seconds)
# SLEEP 020 180 300 600    (default = 20)
#SLEEP 180

# Low line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 106 103 100 097
#    M 177 172 168 182
#    A 092 090 088 086
#    I 208 204 200 196     (default = 0 => not valid)
#LOTRANSFER  208

# High line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 127 130 133 136
#    M 229 234 239 224
#    A 108 110 112 114
#    I 253 257 261 265     (default = 0 => not valid)
#HITRANSFER 253

# Battery change needed to restore power
# RETURNCHARGE 00 15 50 90 (default = 15)
#RETURNCHARGE 15

# Alarm delay 
# 0 = zero delay after pwr fail, T = power fail + 30 sec, L = low battery, N = never
# BEEPSTATE 0 T L N        (default = 0)
#BEEPSTATE T

# Low battery warning delay in minutes
# LOWBATT 02 05 07 10      (default = 02)
#LOWBATT 2

# UPS Output voltage when running on batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 115
#    M 208
#    A 100
#    I 230 240 220 225     (default = 0 => not valid)
#OUTPUTVOLTS 230

# Self test interval in hours 336=2 weeks, 168=1 week, ON=at power on
# SELFTEST 336 168 ON OFF  (default = 336)
#SELFTEST 336

more info:
cat /proc/bus/usb/devices output:
> T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-11-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:10.4
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-11-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.3
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-11-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-11-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0d9f ProdID=0002 Rev= 0.00
S:  Manufacturer=POWERCOM CO., LTD.
S:  Product=USB to Serial
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
E:  Ad=02(O) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc= 11/900 us ( 1%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-11-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=2f11 Rev= 1.00
S:  Manufacturer=Hewlett-Packard
S:  Product=psc 1200 series
S:  SerialNumber=MY44SG10CNT0
C:* #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=cc Prot=00 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 3 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=03(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=84(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=05(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 2 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=d4 Prot=00 Driver=(none)
E:  Ad=05(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  5 Spd=12  MxCh= 4
D:  Ver= 1.01 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=05e3 ProdID=0604 Rev= 0.12
S:  Product=USB Hub
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=255ms

T:  Bus=01 Lev=02 Prnt=05 Port=01 Cnt=01 Dev#= 12 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=040d ProdID=6204 Rev= 0.03
S:  Manufacturer=VIA Technologies Inc.
S:  Product=USB 2.0 IDE Bridge
S:  SerialNumber=000000000001
C:* #Ifs= 1 Cfg#= 2 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=02 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

 
cat /proc/bus/usb/drivers output is:
> total 0
drwxr-xr-x 2 root root 0 2007-03-15 14:37 hiddev
drwxr-xr-x 2 root root 0 2007-03-15 14:37 hub
drwxr-xr-x 2 root root 0 2007-03-15 14:37 libusual
drwxr-xr-x 2 root root 0 2007-03-15 14:37 usb
drwxr-xr-x 2 root root 0 2007-03-15 14:37 usbfs
drwxr-xr-x 2 root root 0 2007-03-15 14:37 usbhid
drwxr-xr-x 2 root root 0 2007-03-15 14:37 usblp
drwxr-xr-x 2 root root 0 2007-03-15 14:37 usb-storage

hope you can make something of this.
thanks

---

### Post by glaucus on 2007-03-18
Hey there. Please post the output of 'lsusb', and 'cat /var/log/apcupsd.conf'. Also, gnome-power-manager (System -> Preferences -> Power Management) SHOULD pick up UPS'. No need to use another program.

---

### Post by odzx on 2007-03-18
here are the outputs:
> oded@oded-desktop:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0d9f:0002 Powercom Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 040d:6204 VIA Technologies, Inc. 
Bus 001 Device 005: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 004: ID 03f0:2f11 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 
cat /var/log/apcupsd.conf says: No such file or directory
i checked if gnome-power-manager picks up the ups by puling the power plug out. it does not seem to notice any difference (still saying "computer running on AC power"

---

### Post by glaucus on 2007-03-19
I'm sorry, I had a typo. That should have been 'cat /var/log/apcupsd.events'

---

### Post by odzx on 2007-03-19
in that case:
>  cat /var/log/apcupsd.events
Sat Mar 17 05:02:51 IST 2007  apcupsd FATAL ERROR in linux-usb.c at line 649
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Mar 17 05:02:51 IST 2007  apcupsd error shutdown completed
Sat Mar 17 05:10:51 IST 2007  apcupsd FATAL ERROR in linux-usb.c at line 649
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Mar 17 05:10:51 IST 2007  apcupsd error shutdown completed
Sat Mar 17 05:47:03 IST 2007  apcupsd FATAL ERROR in linux-usb.c at line 649
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Mar 17 05:47:03 IST 2007  apcupsd error shutdown completed
Sun Mar 18 08:16:39 IST 2007  apcupsd FATAL ERROR in linux-usb.c at line 649
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Mar 18 08:16:39 IST 2007  apcupsd error shutdown completed
Mon Mar 19 05:26:51 IST 2007  apcupsd FATAL ERROR in linux-usb.c at line 649
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 19 05:26:51 IST 2007  apcupsd error shutdown completed

thanks for your help!

---

### Post by glaucus on 2007-03-19
apcupsd doesn't support non-APC UPS' as far as I understand. gnome-power-manager seems to have trouble picking up UPS' that are plugged in after boot (HAL problem w/ power devices?). Try booting up w/ it plugged in, and see if gnome-power-manager will detect it appropriately.

---

### Post by odzx on 2007-03-19
i tried booting up with several times. didn't work.
since either apcupsd and upsmon didn't work I'm guessing the problem is not gnome-power-manager.
could this be a driver problem? :confused:

---

### Post by glaucus on 2007-03-19
Yes, it looks like the lack of support is in HAL. I'm opening up a bug on LP: [https://launchpad.net/ubuntu/+source/hal/+bug/93597](https://launchpad.net/ubuntu/+source/hal/+bug/93597)

Please attach the output of 'lshal' to that bug report, while the UPS is plugged in, and while it is discharging (please note which is which). Thanks!

---

### Post by odzx on 2007-03-19
doing it now

---

### Post by scohar70 on 2007-10-24
> **glaucus said:**
> apcupsd doesn't support non-APC UPS' as far as I understand. gnome-power-manager seems to have trouble picking up UPS' that are plugged in after boot (HAL problem w/ power devices?). Try booting up w/ it plugged in, and see if gnome-power-manager will detect it appropriately.

Do I need to run apcupsd if I have gnome-power-manager?  It seems like gnome-power-manager takes care of everything on my UPS (shutdown, alerts, etc.) without the need for apcupsd, but I can't get any confirmation of that.

---

### Post by yabbadabbadont on 2007-10-24
> **scohar70 said:**
> Do I need to run apcupsd if I have gnome-power-manager?  It seems like gnome-power-manager takes care of everything on my UPS (shutdown, alerts, etc.) without the need for apcupsd, but I can't get any confirmation of that.

apcupsd isn't needed when gnome-power-manager is running.

---

### Post by ferronica on 2007-11-06
Enable UPS discharge alarm not  working in ubuntu 7.10, i am using APC (Bus 002 Device 003: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500)

---

### Post by ferronica on 2007-11-06
here is the screenshot
[http://i20.tinypic.com/egya9z.png[/IMG]"]:confused::confused:]("[IMG)

---

### Post by yabbadabbadont on 2007-11-06
Then file a bug on launchpad...  it won't get fixed otherwise.  ;)

---

