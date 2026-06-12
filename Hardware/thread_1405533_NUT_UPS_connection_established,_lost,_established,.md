---
title: "NUT: UPS connection established, lost, established, etc."
date: 2010-02-12
forum: Hardware
---

### Post by rmcd on 2010-02-12
I have an APC Back-UPS CS 500 which connects via USB. I installed NUT (Karmic amd64). The entry in ups.conf is

> 
[apc]
    driver = usbhid-ups
    port = auto
    desc = "APC Back-UPS CS 500"


After some fiddling I am able to connect to the UPS, and the command "upsc apc" returns the UPS characteristics, so the connection definitely works. However, the UPS connection is then lost and regained, so I get a sequence of messages like this (from syslog):

> 
Feb 12 14:10:38 fin8344 upsmon[2336]: Communications with UPS apc@localhost established
Feb 12 14:11:48 fin8344 upsd[2331]: Data for UPS [apc] is stale - check driver
Feb 12 14:11:50 fin8344 upsd[2331]: UPS [apc] data is no longer stale
Feb 12 14:12:58 fin8344 upsd[2331]: Data for UPS [apc] is stale - check driver
Feb 12 14:13:00 fin8344 upsd[2331]: UPS [apc] data is no longer stale
Feb 12 14:16:56 fin8344 upsd[2331]: Data for UPS [apc] is stale - check driver
Feb 12 14:16:58 fin8344 upsmon[2336]: Poll UPS [apc@localhost] failed - Data stale
Feb 12 14:16:58 fin8344 upsmon[2336]: Communications with UPS apc@localhost lost
Feb 12 14:17:02 fin8344 upsd[2331]: UPS [apc] data is no longer stale
Feb 12 14:17:03 fin8344 upsmon[2336]: Communications with UPS apc@localhost established


Any suggestions for debugging this? I'm not even sure what to look for. Thanks.

---

### Post by rmcd on 2010-02-16
I gave up on NUT and installed apcupsd, which seems to work fine. If you do this, you may need to add the line "apcupsd: 127.0.0.1" to hosts.allow to get things to work.

---

