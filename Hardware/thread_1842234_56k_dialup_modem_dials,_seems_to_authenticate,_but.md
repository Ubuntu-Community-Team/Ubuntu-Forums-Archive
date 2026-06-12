---
title: "56k dialup modem dials, seems to authenticate, but disconnects."
date: 2011-09-11
forum: Hardware
---

### Post by Agent24 on 2011-09-11
I'm trying to get a dialup modem working in Ubuntu. Currently trying in 10.10 but have tried in 11.04 as well, and the problem is the same.

I am using a Dynalink V1456VQE attached to serial port.


I installed gnome-ppp and added myself to the dip and dialout groups.

gnome-ppp detects my modem on /dev/ttyS0.


When I tell it to connect, it dials in, waits a few seconds, then disconnects. The logfile is as follows:

```
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT087303030
--> Waiting for carrier.
ATM1L3DT087303030
CONNECT 46667
--> Carrier detected.  Waiting for prompt.
 
login: 
--> Looks like a login prompt.
--> Sending: *User*
*User*
Password: 
--> Looks like a password prompt.
--> Sending: (password)
Login/Network User: 
--> Looks like a login prompt.
--> Sending: *User*
*User*
CLI - Invalid Argument: *User*
This field is a KEYWORD. The possible values are:
LOGIN                        NETWORK                      PPP
Login/Network User: 
--> Looks like a login prompt.
--> Sending: *User*
*User*
CLI - Invalid Argument: *User*
This field is a KEYWORD. The possible values are:
LOGIN                        NETWORK                      PPP
Login/Network User: 
--> Looks like a login prompt.
--> Sending: *User*
*User*
CLI - Invalid Argument: *User*
This field is a KEYWORD. The possible values are:
LOGIN                        NETWORK                      PPP
Login/Network User: 
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sun Sep 11 16:49:08 2011
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 2351
--> Using interface ppp0
--> Disconnecting at Sun Sep 11 16:49:38 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

```

(*User* is where my username resides, removed for privacy)


What have I done wrong here??

---

