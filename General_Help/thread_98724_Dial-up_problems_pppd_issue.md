---
title: "Dial-up problems:: pppd issue"
date: 2005-12-04
forum: General Help
---

### Post by dewey_au on 2005-12-04
Hi,

I've been searching around this site and the wiki to try and figure out why I cannot connect with my dial-up internet account.

I can hear the modem dial and it seems to get some communication going according to the logs, so I'm ruling out modem driver issues. Fair enough? I've used this particular D-Link external modem with an IPcop linux firewall so I know that it works with linux.

I've been through pppconfig and created a configuration for my account called 'optusnet'... I removed the default named configuration using the pppconfig menus. I don't know whether I should have PAP/CHAT/CHAP selected in pppconfig. I have tried PAP and CHAP, is it worth trying CHAT?

Initially I tried pon/poff but found the logs in /var/log/messages to be pretty unhelpful. Following the advice of other forum members I then went through the process of configuring wvdial on the command line, updated /etc/wvdial.conf with my account, and got more detailed logs of what's going on. I understand that WvDial is a smart dialer that uses pppd underneath? 

After getting nowhere with tweaking the settings in terminal windows for a while I decided to try gnome-ppp as a few people suggested it was pretty idiot-proof. The logs it provides are basically the same as that of WvDial.

```
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT0198331111
--> Waiting for carrier.
ATM1L3DT0198331111
CONNECT 57600
User Access Verification
 Username: username: login: 
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Mon Dec  5 01:17:41 2005
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> pid of pppd: 7245
--> pppd: Z
--> Using interface ppp0
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> Authentication (PAP) started
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> Authentication (PAP) started
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> pppd: Z
--> Disconnecting at Mon Dec  5 01:18:01 2005
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```

* Note: I manually edited /etc/ppp/config and turned on the verbose debugging to try and get more information... It basically just added all those "--> pppd: Z" lines.

Can anybody advise if it's my modem that is hanging up or if it's hanging up at the ISP end? The 'disconnecting...' line makes me think it might be giving up at my end???

dewey

---

### Post by towsonu2003 on 2005-12-04
> --> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.


looks like permissions problem? please post output of 
```
 ls -als /etc/ppp/pap-secrets
ls -als /etc/ppp/chap-secrets

```

also, you are using ```
sudo wvdial
``` right? :)
And also, try including ```
Stupid Mode = yes
``` at the end of /etc/wvdial.conf and see what happens...

---

### Post by dewey_au on 2005-12-04
Hi thanks for the response.

I'm thinking I should just concentrate on getting wvdial configured and working properly... then worry about bringing the settings into Gnome-ppp.


As you suggested, the permission issues were a result of running wvdial as user instead of root. Unfortunately I put the wrong log files in the previous post. 

When run under root I recall (I'm at work now so I can't post the exact output -- will do so later on) that the logs indicate the username and then the password are sent, and not denied. But then end result is exactly the same: wvdial initiates pppd which stays alive for about 15 seconds before hanging up.

```
dwight@schrodinger:~$ ls -als /etc/ppp/pap-secrets
4 -rw-------  1 root root 1702 2005-12-05 02:07 /etc/ppp/pap-secrets
dwight@schrodinger:~$ ls -als /etc/ppp/chap-secrets
4 -rw-------  1 root root 174 2005-12-05 02:07 /etc/ppp/chap-secrets

```

---

### Post by migueljacq on 2005-12-04
Thinking perhaps you should be the owner of the secrets files, and not root, someone correct me if I'm wrong.

---

### Post by towsonu2003 on 2005-12-04
pap and chap should be okay as long as you run wvdial as root (with sudo that is).. wvdial will access them with root provileges... Didyou try stupid mode = yes?

Other than that, have no idea... sorry...

---

