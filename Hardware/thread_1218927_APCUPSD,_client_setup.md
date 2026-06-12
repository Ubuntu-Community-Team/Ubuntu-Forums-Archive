---
title: "APCUPSD, client setup"
date: 2009-07-21
forum: Hardware
---

### Post by gian on 2009-07-21
hello All,

I have one UPS for two servers.

The first one, 192.168.1.124, is directly connected to the UPS via usb cable, and is running apcupsd without problems with the following apcupsd.conf setup:

NETSERVER on
NISIP 127.0.0.1 192.168.1.125
NISPORT 3551

The second one, 192.168.1.125, is the client, which has the following apcupsd.conf setup:

## apcupsd.conf v1.1 ##
UPSCABLE ether
UPSTYPE net
LOCKFILE /var/lock
DEVICE 192.168.1.124:3551
UPSCLASS standalone
UPSMODE disable
POLLTIME 10

When I start apcupsd on the client I get:
Starting UPS power management: Terminating due to configuration file errors.

while apcaccess status
FATAL ERROR in apcaccess.c at line 41
tcp_open: cannot connect to server localhost on port 3551.
ERR=Connection refused

Am I missing something?
I think that the client should not try to connect localhost but rather 192.168.1.124, as specified in DEVICE.

Thanks for your time and support,
-Gian

---

### Post by undertoe on 2009-09-02
I just ran into this problem and noticed my problem was cause by conflicting versions of apcupsd on the server and client.

# apcupsd -V

on both the client and the server see if they match

---

### Post by Nathan.Flow on 2010-06-30
> **gian said:**
> hello All,

I have one UPS for two servers.

The first one, 192.168.1.124, is directly connected to the UPS via usb cable, and is running apcupsd without problems with the following apcupsd.conf setup:

NETSERVER on
NISIP 127.0.0.1 192.168.1.125
NISPORT 3551

The second one, 192.168.1.125, is the client, which has the following apcupsd.conf setup:

## apcupsd.conf v1.1 ##
UPSCABLE ether
UPSTYPE net
LOCKFILE /var/lock
DEVICE 192.168.1.124:3551
UPSCLASS standalone
UPSMODE disable
POLLTIME 10

When I start apcupsd on the client I get:
Starting UPS power management: Terminating due to configuration file errors.

while apcaccess status
FATAL ERROR in apcaccess.c at line 41
tcp_open: cannot connect to server localhost on port 3551.
ERR=Connection refused

Am I missing something?
I think that the client should not try to connect localhost but rather 192.168.1.124, as specified in DEVICE.

Thanks for your time and support,
-Gian

I get the same error on one system using usb and a apc br1500lcd
can you post your apcupsd.conf for me?

---

