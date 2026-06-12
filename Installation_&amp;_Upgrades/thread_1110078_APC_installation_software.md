---
title: "APC installation software?"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by karpat on 2009-03-29
I have a APC Battery backup/surge protection hardware and can't figure out how to install its software which is on a cd.  I"m using ubuntu 8.1

TIA

---

### Post by cariboo on 2009-03-29
The software on the cd isn't needed, there is a utility in the repositories called apcupsd that will control your ups. Once you have installed the package, you have to edit /etc/apcupsd/apcupsd.conf for your type of interface, if you have a usb cable connection edit the following section to reflect your connection:

```
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
DEVICE
```

Once you have edited the configuration file you need to start the daemon:

```
sudo /etc/init.d/apcupsd start
```

to check that everything is running properly in a terminal type:

```
sudo apcaccess
```

and you should get a result that looks something like this:

```
sudo apcaccess
[sudo] password for jim: 
APC      : 001,040,1033
DATE     : Sun Mar 29 12:07:09 PDT 2009
HOSTNAME : willy
RELEASE  : 3.14.5
VERSION  : 3.14.5 (10 January 2009) debian
UPSNAME  : willy
CABLE    : USB Cable
MODEL    : Back-UPS XS  900 
UPSMODE  : Stand Alone
STARTTIME: Fri Mar 06 13:25:48 PST 2009
STATUS   : ONLINE 
LINEV    : 125.0 Volts
LOADPCT  :  17.0 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  53.3 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 3 Minutes
MAXTIME  : 0 Seconds
SENSE    : Medium
LOTRANS  : 088.0 Volts
HITRANS  : 139.0 Volts
ALARMDEL : Always
BATTV    : 27.4 Volts
LASTXFER : Low line voltage
NUMXFERS : 5
XONBATT  : Thu Mar 26 10:33:36 PDT 2009
TONBATT  : 0 seconds
CUMONBATT: 22 seconds
XOFFBATT : Thu Mar 26 10:33:37 PDT 2009
LASTSTEST: Fri Mar 20 22:33:22 PDT 2009
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag
MANDATE  : 2008-04-25
SERIALNO : JB0817017004  
BATTDATE : 2099-00-38
NOMINV   : 120 Volts
NOMBATTV :  24.0 Volts
NOMPOWER : 540 Watts
FIRMWARE : 830.E6 .D USB FW:E6
APCMODEL : Back-UPS XS  900 
END APC  : Sun Mar 29 12:07:54 PDT 2009
```

If you have exim4 installed the ups will email you when the power goes out, and if the outage is long enough it will email you that the power has come back on again.

Jim

---

