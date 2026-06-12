---
title: "dialup modem woes :("
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by blackdalek on 2007-10-22
I'm trying to make a dial-up modem work for a friend who has no broadband access in his area.
I got the followed the dialup modem howto and ran the scanmodem thing which told me to get the hsfconnexant driver from linuxant.. that ran and installed ok.
Now when we use wvdial it does the following...

[COLOR="DeepSkyBlue"]linuxman@netvista:~$ sudo wvdial
Password:
--> WvDial: Internet dialer version 1.56
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT0198331234
--> Waiting for carrier.
ATDT0198331234
CONNECT 460800 
User Access Verification
 Username: username: login: 
--> Carrier detected.  Waiting for prompt.
 Username: username: login: 
--> Looks like a login prompt.
--> Sending: **private_user_name_removed**
**private_user_name_removed**
 Password: password: 
--> Looks like a password prompt.
--> Sending: (password)
% Authorization failed.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT0198331234
--> Waiting for carrier.
NO CARRIER
ATDT0198331234
--> No Carrier!  Trying again.
--> Sending: ATDT0198331234
--> Waiting for carrier.
OK
ATDT0198331234
Caught signal 2:  Attempting to exit gracefully...
--> Disconnecting at Mon Oct 22 17:54:38 2007[/COLOR]

it says Authorization failed every time. Why? The password and username is correct. Anyone know what's going on?

---

### Post by Linicks on 2007-10-22
Usually 'authorisation failed' means that - incorrect credentials.

But anyway, try running wvdial in 'stupid mode' - maybe the ISP is sending something that fubars the handshake.  'stupid mode' tells wvdial to ignore these signals.

Nick

---

### Post by blackdalek on 2007-10-22
Thanks very much.
Adding "Stupid Mode = yes" to the configuration file fixed it.
I successfully connected with wvdial and am posting this message from the dialup connection!

---

