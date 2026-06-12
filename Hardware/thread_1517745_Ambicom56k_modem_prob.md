---
title: "Ambicom56k modem prob"
date: 2010-06-25
forum: Hardware
---

### Post by pythonsyntax on 2010-06-25
> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT715-453-4512
--> Waiting for carrier.
ATM1L3DT715-453-4512
--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Fri Jun 25 13:23:39 2010

i found the driver but i get boot off for some reason.

---

### Post by pythonsyntax on 2010-06-25
anyone?

---

### Post by ieee488 on 2010-06-25
What does your **/etc/wvdial.conf ** look like?

You might need to edit it to get the handshaking to work.

---

### Post by pythonsyntax on 2010-06-25
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = 715-453-4512
ISDN = 0
; Password = 
New PPPD = yes
; Username = invisibleghost
Modem = /dev/modem
Baud = 460800

---

### Post by IcarusR on 2010-06-26
I'm no expert on this but this

> --> Timed out while dialing. Trying again.

suggests to me that something did not happen as expected when dialing. 

Some maybe obvious suggestions...
Is there a dial tone ?
Is it the correct number ?
If you dial the number on a phone does it actually get answered ?
Can you dial out to your mobile ? 

You could try going through this page[URL="http://onlamp.com/pub/a/onlamp/2001/05/10/ppp.html"] [COLOR="Blue"]Troubleshooting ISP Connection Problems[/COLOR]
[/URL]

---

### Post by ieee488 on 2010-06-26
> **pythonsyntax said:**
> [Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = 715-453-4512
ISDN = 0
; Password = 
New PPPD = yes
; Username = invisibleghost
Modem = /dev/modem
Baud = 460800


I find it odd that you are not giving it a password.
I needed to have a password when I was on ATT Worldnet dial-up

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)

---

### Post by pythonsyntax on 2010-06-26
Well ido get a dial tone on gnome-ppp then it boot off again.

---

### Post by pythonsyntax on 2010-06-26
Here the log files

--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT17154534512
--> Waiting for carrier.
ATM1L3DT17154534512
CONNECT 460800 
--> Carrier detected.  Waiting for prompt.
Username: 
--> Looks like a login prompt.
--> Sending: invisibleghost
Username: 
--> Looks like a login prompt.
--> Sending: invisibleghost
invisibleghost
Password: 
--> Looks like a password prompt.
--> Sending: (password)
**************
Username: 
Password: 
--> Looks like a password prompt.
--> Sending: (password)
*******
Username: 
--> Looks like a login prompt.
--> Sending: invisibleghost
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Sat Jun 26 09:47:47 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 4556
--> Using interface ppp0
--> Disconnecting at Sat Jun 26 09:47:56 2010
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.

i am useing gnome-ppp for dialup



If i am right it boot me becuase it login me as guest and passwd guest how can i fix this?

---

### Post by IcarusR on 2010-06-26
Did you enter your correct username & password in the gnome-ppp configuration ? 
If so do they appear correct in the log file ?
Check to see if correct details in /etc/wvdial.conf

---

### Post by pythonsyntax on 2010-06-26
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
New PPPD = yes
Phone = 17154534523
Modem = /dev/modem
Username = invisibleghost
Password = 
Baud = 460800


It put my password in the usr name when it dial.

---

### Post by IcarusR on 2010-06-26
Could try renaming wvdial.conf (ie wvdial.conf.old) & start again with gnome-ppp which should recreate it.
If it stuffs up you can always go back to origional wvdial.conf

---

### Post by ieee488 on 2010-06-26
> **pythonsyntax said:**
> 
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.


Start up Terminal window and type the following
```

sudo chmod a+rw /etc/ppp/pap-secrets
sudo chmod a+rw /etc/ppp/chap-secrets

```

Also, make sure gnome-ppp is set to do pap/chap

---

### Post by IcarusR on 2010-06-26
According to post 8 on this [[COLOR="Navy"]_bug report_[/COLOR]]("Warning: Could not modify /etc/ppp/pap-secrets: Permission denied") "Warning: Could not modify /etc/ppp/pap-secrets: Permission denied" is normal & not a problem !
But people on there have changed attribs to 777 & got it to work.

---

### Post by pythonsyntax on 2010-06-26
it work now thank alot for the help:)

---

