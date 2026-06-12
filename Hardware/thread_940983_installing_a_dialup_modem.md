---
title: "installing a dialup modem"
date: 2008-10-07
forum: Hardware
---

### Post by Canuck.old on 2008-10-07
Hello one& all
  I am helping a buddy by installing a dialup modem (3com 56K Fax Modem)

Everything goes fine - except it does not work ;)
Here is a WVdial output


sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT2504020078
--> Waiting for carrier.
ATDT2504020078
CONNECT 49333/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
Telus PLANet CLGRTNT2
login:
--> Looks like a login prompt.
--> Sending: bmulley
bmulley
Password:
--> Looks like a password prompt.
--> Sending: (password)
AiiNet:>
--> Hmm... a prompt.  Sending "ppp".
ppp
    Entering PPP Session.
    IP address is 161.184.42.165
    MTU is 1524.
~[7f]}#@!}!}!} %} }$} } }!}$}%t}"}&} } } } }'}"}(}"}1}$}%t}3}+}!clgr_tnt[}1~
--> PPP negotiation detected.
--> Starting pppd at Sun Oct  5 10:24:31 2008
--> Pid of pppd: 20078
--> Using interface ppp0
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> local  IP address 161.184.42.165
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> remote IP address 161.184.0.198
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> primary   DNS address 198.80.55.1
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> secondary DNS address 198.161.156.1
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
Caught signal 2:  Attempting to exit gracefully...
--> Terminating on signal 15
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> Connect time 9.7 minutes.
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> pppd: &#65533;&#65533;[06][08]H&#65533;[06][08]
--> Disconnecting at Sun Oct  5 10:34:16 2008

I sent the sig 15

Help an old man - fix this problem.

Thank you for your time.

D.K. Robinson

oops my OS is 2.6.24-19-grneric

---

