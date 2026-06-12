---
title: "modem hangs up a lot"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by cobelloy on 2005-08-17
hi again, my modem seems to hang up a lot, especially when I have a lot of activity on the line, such as filesharing (amule) and downloading packages with synaptic or apt, this time I read through the log to see what it said, I had copied the output, but now nothing will paste, so I will work from memory, there was some mention of secrets having global access, and some mention of ethernet interface not doing something, also sending some echo requests with no response and eventually the ppp daemon dying unexpectedly.

My pap and chap secrets files have rwx access for all users, I have no active ethernet, and my modem is an ISDN 128/64k modem open technologies NT1plusII

when I set up dial up it was via wvdial (command-line) and then I followed some instructions I have lost the address for that told me how to set up non-root dial out, basically everything involved in dial-out now belongs to the group "modem" instead of root, and I changed some permissions such as the secrets files and /var/lock I think also.

Does anyone have any ideas?

---

### Post by cobelloy on 2005-08-17
I captured the last log:

Aug 17 18:31:32 localhost pppd[28110]: pppd 2.4.2 started by cobelloy, uid 1000
Aug 17 18:31:32 localhost pppd[28110]: Using interface ppp0
Aug 17 18:31:32 localhost pppd[28110]: Connect: ppp0 <--> /dev/ttyS0
Aug 17 18:31:34 localhost pppd[28110]: CHAP authentication succeeded: 
Aug 17 18:31:34 localhost pppd[28110]: Cannot determine ethernet address for proxy ARP
Aug 17 18:31:34 localhost pppd[28110]: local  IP address 144.139.109.237
Aug 17 18:31:34 localhost pppd[28110]: remote IP address 139.134.14.178
Aug 17 18:31:34 localhost pppd[28110]: primary   DNS address 203.49.70.20
Aug 17 18:31:34 localhost pppd[28110]: secondary DNS address 139.134.2.190
Aug 17 18:31:42 localhost pppd[28110]: Warning - secret file /etc/ppp/chap-secrets has world and/or group access
Aug 17 19:25:32 localhost pppd[28110]: No response to 4 echo-requests
Aug 17 19:25:32 localhost pppd[28110]: Serial link appears to be disconnected.
Aug 17 19:25:32 localhost pppd[28110]: Connect time 54.0 minutes.
Aug 17 19:25:32 localhost pppd[28110]: Sent 2859724 bytes, received 20406474 bytes.
Aug 17 19:25:33 localhost pppd[28110]: Hangup (SIGHUP)
Aug 17 19:25:33 localhost pppd[28110]: Modem hangup
Aug 17 19:25:33 localhost pppd[28110]: Connection terminated.
Aug 17 19:25:33 localhost pppd[28110]: Exit.

does anyone know what it means?

---

