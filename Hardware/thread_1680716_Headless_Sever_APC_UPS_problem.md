---
title: "Headless Sever APC UPS problem"
date: 2011-02-03
forum: Hardware
---

### Post by sidcypher on 2011-02-03
Recently had to replace my old junky 4min UPS due to hardware failure.. Rarely have power issues, and when we do it is a simple minute or two... Recently due to the weather conditions we have gone into 1hr rolling blackouts. Replaced my old APC w/no link to a new APC BX1300G (1300VA w/pretty LCD Display and 10 plugs)

I am getting a failure in the log file and have been unable to resolve it thus far, went through the entire [apcupsd manual]("http://www.apcupsd.org/manual/manual.html") on webpage as well as Ubuntu's UPS guide, and many posts in this forum with no luck...

Keep getting this over and over...

```

Wed Feb 02 22:19:32 CST 2011  Valid lock file for pid=4354, but not ours pid=52$
Wed Feb 02 22:19:32 CST 2011  apcupsd FATAL ERROR in device.c at line 70
Unable to create UPS lock file.
  If apcupsd or apctest is already running,
  please stop it and run this program again.
Wed Feb 02 22:19:32 CST 2011  Valid lock file for pid=4354, but not ours pid=52$
Wed Feb 02 22:19:32 CST 2011  apcupsd error shutdown completed

```

Part of the apcupsd.conf as puTTY wasn't wanting to copy and paste properly... and there is no GUI on server...

```
## apcupsd.conf v1.1 ##
#
#  for apcupsd release 3.14.4 (18 May 2008) - debian
#
# "apcupsd" POSIX config file

#
# ========= General configuration parameters ============
#

# UPSNAME xxx
#   Use this to give your UPS a name in log files and such. This
#   is particulary useful if you have multiple UPSes. This does not
#   set the EEPROM. It should be 8 characters or less.
#UPSNAME BeastBat

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
# usb       <BLANK>          Most new UPSes are USB. A blank DEVICE
#                            setting enables autodetection, which is
#                            the best choice for most installations.
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
#                            rfc1628 UPS-MIB. You usually want "APC".
#                            Port is usually 161. Community is usually
#                            "private".
#
# dumb      /dev/tty**       Old serial character device for use
#                            with simple-signaling UPSes.
#
# pcnet    ipaddr:username:passphrase
#                            PowerChute Network Shutdown protocol
#                            which can be used as an alternative to SNMP
#                            with AP9617 family of smart slot cards.
#                            ipaddr is the IP address of the UPS mgmt
#                            card. username and passphrase are the
#                            credentials for which the card has been
#                            configured.
#
UPSTYPE usb
#DEVICE

# POLLTIME <int>
#   Interval (in seconds) at which apcupsd polls the UPS for status. This
#   setting applies both to directly-attached UPSes (UPSTYPE apcsmart, usb,
#   dumb) and networked UPSes (UPSTYPE net, snmp). Lowering this setting
#   will improve apcupsd's responsiveness to certain events at the cost of
#   higher CPU utilization. The default of 60 is appropriate for most
#   situations.
POLLTIME 60

# LOCKFILE <path to lockfile>
#   Path for device lock file. Not used on Win32.
LOCKFILE /var/lock

# SCRIPTDIR <path to script directory>
#   Directory in which apccontrol and event scripts are located.
SCRIPTDIR /etc/apcupsd

# PWRFAILDIR <path to powerfail directory>
#   Directory in which to write the powerfail flag file. This file
#   is created when apcupsd initiates a system shutdown and is
#   checked in the OS halt scripts to determine if a killpower
#   (turning off UPS output power) is required.
PWRFAILDIR /etc/apcupsd

# NOLOGINDIR <path to nologin directory>
#   Directory in which to write the nologin file. The existence
#   of this flag file tells the OS to disallow new logins.
NOLOGINDIR /etc

```

Random info of stuff from the apcupsd manual (commands I tried)

```
james@beast:~$ cat /proc/bus/usb/devices
cat: /proc/bus/usb/devices: No such file or directory
james@beast:~$ ps ax | grep devs
29816 pts/1    R<+    0:00 grep devs


```

What does work...

A simple communications test by unplugging the link cable for a bit... Did not alert that it was unplugged but did notify of reconnection..
Communications restored with UPS beast.**xxx**.**xxx**.net


```
james@beast:~$ apcaccess
APC      : 001,038,0968
DATE     : Wed Feb 02 22:48:05 CST 2011
HOSTNAME : beast.**xxx**.**xxx**.net
RELEASE  : 3.14.4
VERSION  : 3.14.4 (18 May 2008) debian
UPSNAME  : beast.gateway.2wire.net
CABLE    : USB Cable
MODEL    : Back-UPS BX1300G
UPSMODE  : Stand Alone
STARTTIME: Wed Feb 02 22:10:47 CST 2011
STATUS   : ONLINE
LINEV    : 123.0 Volts
LOADPCT  :   2.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT : 117.8 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
SENSE    : Medium
LOTRANS  : 088.0 Volts
HITRANS  : 139.0 Volts
ALARMDEL : Always
BATTV    : 27.0 Volts
LASTXFER : No transfers since turnon
NUMXFERS : 0
TONBATT  : 0 seconds
CUMONBATT: 0 seconds
XOFFBATT : N/A
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag
MANDATE  : 2010-05-21
SERIALNO : 3B1021X52475
BATTDATE : 2001-09-25
NOMINV   : 120 Volts
NOMBATTV :  24.0 Volts
NOMPOWER : 780 Watts
FIRMWARE : 864.L3 .D USB FW:L3
APCMODEL : Back-UPS BX1300G
END APC  : Wed Feb 02 22:48:38 CST 2011

```

This WAS working until the last reboot... haven't been able to get into it since...

apctest requires that apcupsd is NOT running so I showed that I did attempt to stop the service..

```
james@beast:~$ sudo service apcupsd stop
Stopping UPS power management: No process in pidfile `/var/run/apcupsd.pid' found running; none killed.
apcupsd.
james@beast:~$ sudo service apctest stop
apctest: unrecognized service
james@beast:~$ sudo apctest


2011-02-02 22:58:56 apctest 3.14.4 (18 May 2008) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
apctest FATAL ERROR in device.c at line 70
Unable to create UPS lock file.
  If apcupsd or apctest is already running,
  please stop it and run this program again.
apctest error termination completed
james@beast:~$

```

Got apctest to work.. now displays... 

```
james@beast:~$ sudo apctest


2011-02-02 23:43:19 apctest 3.14.4 (18 May 2008) debian
Checking configuration ...
Attached to driver: usb
sharenet.type = DISABLE
cable.type = USB_CABLE

You are using a USB cable type, so I'm entering USB test mode
mode.type = USB_UPS
Setting up the port ...
Hello, this is the apcupsd Cable Test program.
This part of apctest is for testing USB UPSes.

Getting UPS capabilities...SUCCESS

Please select the function you want to perform.

1)  Test kill UPS power
2)  Perform self-test
3)  Read last self-test result
4)  Change battery date
5)  View battery date
6)  View manufacturing date
7)  Set alarm behavior
8)  Set sensitivity
9)  Set low transfer voltage
10) Set high transfer voltage
11) Quit

Select function number:

```
USB listing....

```
james@beast:~$ ls -l /sys/bus/usb/drivers
total 0
drwxr-xr-x 2 root root 0 2011-02-02 23:00 hiddev
drwxr-xr-x 2 root root 0 2011-02-02 23:00 hub
drwxr-xr-x 2 root root 0 2011-02-02 23:00 usb
drwxr-xr-x 2 root root 0 2011-02-02 23:00 usbfs
drwxr-xr-x 2 root root 0 2011-02-02 23:00 usbhid

```

Of course when I unplugged from the wall, it just straight turned off my server, no shutdown... just boom off... plugged back into wall... entered BIOS and unplugged... remained on.. So I figure I have a timer somewhere off..

Any Ideas? Or need me to post any additional info?

---

### Post by tgalati4 on 2011-02-03
sudo /etc/init.d/apcupsd restart
reboot

Pull the usb cable then check the logs.  If OK, then reconnect and check the logs.  Then test the ups by flipping the breaker.  Don't pull the plug, you need to keep the ground connected to avoid damage.

---

