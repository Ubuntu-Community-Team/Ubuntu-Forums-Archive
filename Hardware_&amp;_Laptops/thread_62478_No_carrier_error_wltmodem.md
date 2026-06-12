---
title: "No carrier error w/ltmodem"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by cai on 2005-09-04
I just installed Ubuntu 5.04 and have installed the driver for my Lucent/Agare WinModem (ubuntu-ltmodem-2.6.10-5-386_8.31a13_i386.deb). When I use wvdial to try and connect, I get the same "no carrier" everytime.

```
--> WvDial: Internet dialer version 1.54.0
--> 
Initializing modem.
--> 
Sending: ATZ
ATZ
OK
--> 
Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> 
Modem initialized.
--> 
Sending: ATDT5140040
--> 
Waiting for carrier.
ATDT5140040
--> 
Timed out while dialing.  
Trying again.
--> 
Sending: ATDT5140040
--> 
Waiting for carrier.

NO CARRIER
ATDT5140040
--> 
No Carrier!  Trying again.
--> 
Sending: ATDT5140040
--> 
Waiting for carrier.

NO CARRIER
ATDT5140040
--> 
No Carrier!  Trying again.
--> 
Sending: ATDT5140040
--> 
Waiting for carrier.

NO CARRIER
ATDT5140040
--> 
No Carrier!  Trying again.
--> 
Sending: ATDT5140040
--> 
Waiting for carrier.
NO CARRIER
ATDT5140040
--> 
``` 

etc, etc until I Ctrl-C to kill wvdial. The modem connects just fine with Fedora Core and Windows XP. Is there some obscure setting I haven't set up? Any help would be much appreciated. 

Thanks!

---

### Post by npcomplete on 2007-05-12
Hi cai,
  I encountered the same problem under Ubuntu 7.04, I found that after executing the following:

```
sudo /etc/init.d/sl-modem-dameon restart
```

Everything works fine again. However, it seems that you have to restart the daemon every time when you want to dial...

---

### Post by towsonu2003 on 2007-05-12
did you try the tweaks mentioned [here]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9")?

I used to dialup with an slmodem: it used to took me anywhere between 5 to 30 minutes to dialup because of the "no carrier" error. My solution was to keep trying until successful.

---

### Post by tinsami1 on 2007-06-12
After googling around for a couple of hours, this did the trick!  Now my modem is dialing out. :KS :KS :KS :KS :KS

Mine is a built-in ATI SB400 AC'97 Modem in an IBM Thinkpad R51e.

I would file this as a bug but it seems a lot of slmodem-related entries are not being given attention.  At least, there's this workaround.

Kudos!

--- mike t.

---

