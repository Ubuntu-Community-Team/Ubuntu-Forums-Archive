---
title: "UPS with USB in ubuntu 8.10 64bit"
date: 2008-11-18
forum: General Help
---

### Post by dmanbuhnik on 2008-11-18
i'm going to cry....
it's been 3 days now and i still didn't get my UPS to work in linux ](*,)

i got an USB UPS (its from an Israeli company call 'Advice') that has the hardware of 'powercom' inside, at least i think so

```
$ lsusb
...
Bus 006 Device 003: ID 0d9f:0002 Powercom Co., Ltd
...

```

i'm trying to work with nut but i didn't mange to work with the other options as well
also, in the gnome-power-management there is no 'UPS' tab (it should be, right?)

right now when i'm trying to start nut i will get:
```
$ sudo upsdrvctl start advice
Network UPS Tools - UPS driver controller 2.2.2
Network UPS Tools - PowerCom and similars protocol UPS driver $ Revision: 0.5 $ (2.2.2)


Unable to open usb: No such file or directory

Things to try:

 - Check 'port=' in ups.conf

 - Check owner/permissions of all parts of path

Fatal error: unusable configuration
Driver failed to start (exit status=1)

```
any help will be great
Thx in advance

---

### Post by Th3Professor on 2008-11-18
Ah you reminded me... I need to get my Tripp Lite UPS (the USB on it) set up with my system! It looks like you're using a different UPS though I'm curious to hear how it turns out for you.

---

### Post by dmanbuhnik on 2008-11-20
bump

anyone?

---

### Post by Th3Professor on 2008-11-20
<bump>
I'll give you another bump. I, too, would like to know more about this. I haven't set up the USB with my UPS & operating systems yet, though I suspect any helpful replies in this thread will come in handy for my Tripp Lite (although it's a different brand than yours).
</bump>

---

### Post by dmanbuhnik on 2008-11-20
is you UPS listed in nut supported devices?
([http://eu1.networkupstools.org/compat/](http://eu1.networkupstools.org/compat/))

if so then the only diffrence between me and u is the driver that nut will use => solving my problem will solve your problem

hopfully
if anyone would answer

---

### Post by Th3Professor on 2008-11-20
Nope... not exactly. I have "SMART1000LCD" model, which is not listed, though others very similar are listed. The item I have says the USB feature works with Linux... though that link you provided doesn't list it.

---

### Post by tgalati4 on 2008-11-20
I've only used apcupsd which is the daemon that monitors APC smartUPS for ethernet, serial, and USB.  Works well and has shut down my machines many times.

tgalati4@tubuntu2:/var/log$ cat apcupsd.status
APC      : 001,021,0583
DATE     : Mon Oct 20 10:59:08 PDT 2008
HOSTNAME : tubuntu2
RELEASE  : 3.12.4
VERSION  : 3.12.4 (19 August 2006) debian
UPSNAME  : TerryLab
CABLE    : Custom Cable Simple
MODEL    : DUMB UPS Driver
UPSMODE  : Net Master
STARTTIME: Mon Oct 20 10:59:01 PDT 2008
SHARE    : NetworkUPS
STATUS   : ONLINE SLAVEDOWN
MBATTCHG : 5 Percent
MINTIMEL : 5 Minutes
MAXTIME  : 30 Seconds
NUMXFERS : 1
XONBATT  : Sat Nov 15 09:08:22 PST 2008
TONBATT  : 0 seconds
CUMONBATT: 1 seconds
XOFFBATT : Sat Nov 15 09:08:23 PST 2008
STATFLAG : 0x07000808 Status Flag
END APC  : Thu Nov 20 13:54:15 PST 2008

----------------
A portion of apcupsd.events:

Fri Jun 27 15:41:34 PDT 2008  Power failure.
Fri Jun 27 15:41:54 PDT 2008  Running on UPS batteries.
Fri Jun 27 15:42:05 PDT 2008  Mains returned. No longer on UPS batteries.
Fri Jun 27 15:42:05 PDT 2008  Power is back. UPS running on mains.
Fri Oct 03 10:00:16 PDT 2008  apcupsd exiting, signal 15
Fri Oct 03 10:00:16 PDT 2008  apcupsd shutdown succeeded
Fri Oct 03 10:04:23 PDT 2008  apcupsd 3.12.4 (19 August 2006) debian startup succeeded
Fri Oct 03 10:04:24 PDT 2008  Connect to slave hpubuntu failed. ERR=No route to host
Fri Oct 03 10:07:29 PDT 2008  apcupsd exiting, signal 15
Fri Oct 03 10:07:29 PDT 2008  apcupsd shutdown succeeded
Fri Oct 03 11:39:57 PDT 2008  apcupsd 3.12.4 (19 August 2006) debian startup succeeded
Fri Oct 03 11:39:58 PDT 2008  Connect to slave hpubuntu failed. ERR=No route to host
Mon Oct 06 14:51:19 PDT 2008  apcupsd exiting, signal 15
Mon Oct 06 14:51:19 PDT 2008  apcupsd shutdown succeeded
Mon Oct 06 15:02:33 PDT 2008  apcupsd 3.12.4 (19 August 2006) debian startup succeeded
Mon Oct 06 15:02:34 PDT 2008  Connect to slave hpubuntu failed. ERR=No route to host
Mon Oct 20 10:49:16 PDT 2008  apcupsd exiting, signal 15
Mon Oct 20 10:49:16 PDT 2008  apcupsd shutdown succeeded
Mon Oct 20 10:59:03 PDT 2008  apcupsd 3.12.4 (19 August 2006) debian startup succeeded
Mon Oct 20 10:59:04 PDT 2008  Connect to slave hpubuntu failed. ERR=No route to host
Sat Nov 15 09:08:22 PST 2008  Power failure.
Sat Nov 15 09:08:23 PST 2008  Power is back. UPS running on mains.

So, if you can't get your Advice/Powercomm UPS to work, you might want to return it a nd get an APC UPS instead.

Using apcupsd, you only need one machine (probably a 24/7 server) connected via cable.  The rest of the machines can be hooked up to their own UPS's without a cable and they will be shutdown through a network broadcast.  Assuming your LAN is plugged into the server UPS.

Another option is to keep your current Advice UPS and place it on a desktop machine and get another UPS (APC brand) and use that for the cable connection and 24/7 power monitor with network shutdown broadcast enabled.  This allows you to use unsupported UPS's with all of your Linux boxes because you only need one APC (or other supported UPS) connected and monitored.

Good luck.  Sorry that I couldn't be of more help.

---

### Post by dmanbuhnik on 2008-11-20
i got my UPS for 2 years now.
he is working fine and i don't/can't replace it

this should be easy as powercomm is supported in 'nut'

---

