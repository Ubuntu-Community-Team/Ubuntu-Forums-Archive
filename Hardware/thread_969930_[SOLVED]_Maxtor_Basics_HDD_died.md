---
title: "[SOLVED] Maxtor Basics HDD died"
date: 2008-11-03
forum: Hardware
---

### Post by bobsta101 on 2008-11-03
Hey I have been using a Maxtor Basics 500G External Desktop Hard drive.
it was plugged into my PC working, all mounted and accessible. I left it and cmae back a few hours later and it was no longer mounted and I cant get it to mount.

I tried using a GParted live CD to see if I could access the Hard drive from there but no luck. ( GParted took longer to boot showing this message" usb 1-4: device descriptor read /64, error -110" which doesn't normally show, and Udev took a while to load.

I have tried plugging it into a windows machine and it Says it cannot recognise the device.

Any help appreciated.

---

### Post by ezeze5000 on 2008-11-03
If you only have one drive on the system, check the jumpers on your drive.
If it is set to cable select, try changing it to the master setting.
I have had drives that would start working after doing this.

I hope this helps.

---

### Post by bobsta101 on 2008-11-03
Hey not sure if I made myself clear. it is an External HDD, all cables are secure.

---

### Post by tgalati4 on 2008-11-03
Post the output from a terminal:

>dmesg | tail

---

### Post by bobsta101 on 2008-11-03
[12172.697289] Unknown OutputIN= OUT=vmnet2 SRC=192.168.72.1 DST=192.168.72.255 LEN=202 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=182 
[12172.697330] Unknown OutputIN= OUT=vmnet8 SRC=172.16.56.1 DST=172.16.56.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=181 
[12202.679247] Unknown OutputIN= OUT=vmnet2 SRC=192.168.72.1 DST=192.168.72.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=181 
[12202.679278] Unknown OutputIN= OUT=vmnet8 SRC=172.16.56.1 DST=172.16.56.255 LEN=200 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=180 
[12203.682455] Unknown OutputIN= OUT=vmnet2 SRC=192.168.72.1 DST=192.168.72.255 LEN=202 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=182 
[12203.682498] Unknown OutputIN= OUT=vmnet8 SRC=172.16.56.1 DST=172.16.56.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=181 
[12233.660252] Unknown OutputIN= OUT=vmnet2 SRC=192.168.72.1 DST=192.168.72.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=181 
[12233.660284] Unknown OutputIN= OUT=vmnet8 SRC=172.16.56.1 DST=172.16.56.255 LEN=200 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=180 
[12234.663577] Unknown OutputIN= OUT=vmnet2 SRC=192.168.72.1 DST=192.168.72.255 LEN=202 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=182 
[12234.663609] Unknown OutputIN= OUT=vmnet8 SRC=172.16.56.1 DST=172.16.56.255 LEN=201 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=181 
bobsta@bobsta-desktop:~$

---

### Post by bobsta101 on 2008-11-06
hmmm external HDD seemed fine after leaving unplugged for a while and letting it cool down.. strange

cheers for the help anyway guys.

bobsta

---

