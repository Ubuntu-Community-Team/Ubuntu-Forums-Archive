---
title: "Sigmatel Stir4200 USB IRDA Dongle"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by pyronicte on 2005-11-24
Hi

I have an usb dongle for IRDA model Stir4200 from Sigmatel. In WindowsXP it works fine, but under Ubuntu I can't do anything with it. 
I have installed irda-utils, it's detected and assumed as irda1, I attach with irattach irda1 -s,  modprobe ircomm and ircomm-tty, and use irdadump. No connection possible.

How I configure it? What GUI I can use to link with my Siemens S65 phone?

---

### Post by pyronicte on 2005-11-24
Perhaps Am I the only ubunter who have sigmatel hardware missworking?

Or nobody buy sigmatel hardware pieces?

---

### Post by pyronicte on 2005-11-25
Hello again

I have solve the irda question on my own, and I put it at here for others like me.

The trouble is the ubuntu startup at irda-utils. It detects and put irda in irda1 interface, and it doesn't correct. All you have to do is to run command "irattach irda0 -s" and you can connect to others devices.

In order to friendly access my siemens s65 movile, I also tried obextool, and it works fine.

Bye

---

### Post by spork on 2006-02-27
I hope this may help anyone else having problems with these dongles ...
I'm using ubuntu 5.10 on a HP pavilion ze2000 (ze2310ea to be exact)
these are the packages I've installed
irda-utils
synce-dccm
synce-serial

after installing synce-serial the resulting contents of /etc/synce are :
dnsip:192.168.0.1
interface:/dev/ircomm0
localip:192.168.131.102
remoteip:192.168.131.201


to get it working with my IPAQ/WINCE I had to:
modprobe crc_ccitt
modprobe irda
modprobe stir4200
modprobe ircomm 
modprobe ircomm_tty 
irattach irda0 -s 
synce-serial-start

then hit the "IR ActiveSync" icon on the IPAQ (start/programs/connections)

the connection is dropped from time to time and so far all I can do to get it going again is to remove and replace the dongle then:

synce-serial-abort
killall -9 irattach

rmmod ircomm_tty
rmmod ircomm
rmmod stir4200
rmmod irda
rmmod crc_ccitt

modprobe crc_ccitt
modprobe irda
modprobe stir4200
irattach irda0 -s &&\
modprobe ircomm &&\
modprobe ircomm_tty &&\
synce-serial-start


all this can be put into a simple script ...

---

