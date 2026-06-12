---
title: "ftp through router"
date: 2009-09-07
forum: Hardware
---

### Post by shookees on 2009-09-07
Hello,
I have a router that has it's own network(the ones 192.168.1.***) and I'm interested in releasing a FTP server but I have noticed that I can only apply it to localhost (because I don't know how to set my router to let external FTP connections).
Anybody  could help me with that?
some info:
router connection type: DHCP
router name: linksys g wrt54gl

thanks,
shookees

---

### Post by shookees on 2009-09-07
bump :S

---

### Post by Whiffle on 2009-09-07
First you need to assign your server a static IP address:
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

and then you need to forward port 21 to your server, here is a guide for that router on the subject:
[http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/default.htm)

---

### Post by str3zz on 2009-09-07
Hello,

as Whiffle already mentioned you need static IP (so you can easily remember your public IP address) or you can register to some dynamic DNS server (most of router do support update of dynamic DNS service automatically, when new IP is assigned from DHCP - quite often it's dyndns.com)

regarding the ports for ftp server
you need to open port 21 for ftp and 20 for ftpdata (ftp connection in active mode)
also you need to configure your ftp server and specify range of passive ports which should be used by ftp server when passive connection is requested (use high port range, where you do not run anything else)
also this passive port range needs to be open on router/firewall

at the end I would say, that there is too much effort to get ftp working as we do have sftp (which is part of sshd - port 22), but only in case you do not require anonymous access 

just a note - all the port should be open for both - tcp & udp

cheers,
str3zz

---

### Post by shookees on 2009-09-14
thank you! :)

---

