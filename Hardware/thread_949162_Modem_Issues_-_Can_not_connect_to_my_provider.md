---
title: "Modem Issues - Can not connect to my provider"
date: 2008-10-15
forum: Hardware
---

### Post by J_dillinger on 2008-10-15
I have a Dell E1505 with Ubuntu 8.04 running on it.  I have installed hsfmodem_7.68.00.09oem_i386.deb and I think the modem is working but it seems to be failing the PAP and/or CHAP authentication.  The following is the information I receive when the Modem is connecting...

--> Modem initialized.
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT*70, 218 0079
--> Waiting for carrier.
ATDT*70, 218 0079
CONNECT 57600 
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas21.phx1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: ***Login Name Omitted***
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Fri Sep 26 07:51:14 2008
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> 
--> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> 
--> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 9059
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 4.240.60.131
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 63.215.26.149
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 207.69.188.187
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 207.69.188.186
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]

I have also tried to modify the pppoeconf file, but have not been able to properly configure the authentication process.

Thanks

---

