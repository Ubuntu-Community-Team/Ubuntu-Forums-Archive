---
title: "Problem setting up UPS using NUT on Ubuntu 7.10?"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by mutineer612 on 2008-02-15
I am trying to configure a USB Powerware 5110 UPS in Ubuntu 7.10.  It looks like I'm able to see the UPS via the USB connection, Yet I'm getting errors when I start nut using "/etc/init.d/nut start", or run "upsmon".  I've configured the files to the best of my knowledge correctly.  I'm not sure what I'm missing.  I've attached my configuration, command output and errors below and would appreciate any help from the community. 

 root@ubuntu:/etc/nut# lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0592:0002 Powerware Corp. 
Bus 001 Device 001: ID 0000:0000

root@ubuntu:/etc/nut# ls -l
total 16
-rw-r--r-- 1 root root  41 2008-02-15 20:42 ups.conf
-rw-r--r-- 1 root root  73 2008-02-15 20:15 upsd.conf
-rw-r--r-- 1 root root 147 2008-02-15 20:41 upsd.users
-rw-r--r-- 1 root root 246 2008-02-15 20:40 upsmon.conf

root@ubuntu:/etc/nut# cat ups.conf 
[pw5110]
driver = bcmxcp_usb
port = auto

root@ubuntu:/etc/nut# cat upsd.conf 
ACL all 0.0.0.0/0
ACL localhost 127.0.0.1/32
ACCEPT localhost
REJECT all

root@ubuntu:/etc/nut# cat upsd.users 
[admin]
password = password0
allowfrom = localhost
actions = SET
instcmds = ALL

[monuser]
password = password1
allowfrom = localhost 
upsmon master

root@ubuntu:/etc/nut# cat upsmon.conf
MINSUPPLIES 1
SHUTDOWNCMD "/sbin/shutdown -h +0"
POLLFREQ 5
POLLFREQALERT 5
HOSTSYNC 15
DEADTIME 15
POWERDOWNFLAG /etc/killpower
RBWARNTIME 43200
NOCOMMWARNTIME 300
FINALDELAY 5
RUN_AS_USER root
MONITOR pw5110@localhost 1 monuser password1 master

**The error I get when running upsmon:**

root@ubuntu:/etc/nut# upsmon
Network UPS Tools upsmon 2.0.5
Using power down flag file /etc/killpower

UPS: pw5110@localhost (master) (power value 1)
                                                                               
Broadcast Message from root@ubuntu                                     
        (somewhere) at 21:07 ...                                               
                                                                               
Communications with UPS pw5110@localhost lost                                  
                                                                               
                                                                               
Broadcast Message from root@ubuntu                                 
        (somewhere) at 21:07 ...                                               
                                                                               
UPS pw5110@localhost is unavailable

---

### Post by ac4000 on 2008-06-29
If it's still not working, try using the newhidups driver.  Switching from hidups to that driver worked with my TrippLite OMNI1000LCD, so it may be a shot in the dark for other types, but I did have that same error and now everything works.

---

