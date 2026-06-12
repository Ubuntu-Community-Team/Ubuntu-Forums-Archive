---
title: "Dial Up Connection to the Intenet - Configure or Disable the Firewall"
date: 2008-09-29
forum: Hardware
---

### Post by J_dillinger on 2008-09-29
I have been trying to get my Dell e1505 connected to the internet with a Dial up connection.  After Installing the drivers for the conexant modem ( libc6-dev_2.3.6-0ubuntu20_i386.deb / hsfmodem_7.68.00.09oem_i386.deb) I have managed to connect to the internet and receive an IP Address ect.. from my service provider.  I am, however, still unable to connect to the internet. and was wandering if a firewall needs to be configured to allow the connection to receive information from the internet.  Currently the connection work fine through wireless, but I can not ping out when the internet is connected or connect to a web site when firefox is opened.

I would also like to point out in this question that the ubuntu forums recommended by dell tech support were very helpful in finding the proper drivers if anybody else is trying to connect to the internet with dial up.

I am having some problem with connecting through a dial up connection - I know loose the dinosaur, but I am receiving the following with vwdial...

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
--> Carrier detected. Waiting for prompt.
Level 3 Comm nas21.phx1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: ***Login Name Omitted***
--> Don't know what to do! Starting pppd and hoping for the best.
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
--> local IP address 4.240.60.131
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 63.215.26.149
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> primary DNS address 207.69.188.187
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 207.69.188.186
--> pppd: &#65533;&#65533;&#65533;&#65533;&#1064;[06][08]&#65533;&#65533;[06][08]

The modem seems to be connected, but I still can not resolve websites in firefox, do I have a problem with my configuration?

---

