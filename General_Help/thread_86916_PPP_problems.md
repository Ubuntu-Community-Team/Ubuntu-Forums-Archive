---
title: "PPP problems"
date: 2005-11-06
forum: General Help
---

### Post by leetcharmer on 2005-11-06
I've been trying to connect online with an internal modem, I have gnome-ppp installed and that's what I've been using for this.  The following is the furthest I've been able to get, but it won't stay connected for longer than 30 seconds.

```
GNOME PPP: STDERR: ttySHSF0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
GNOME PPP: Connecting...
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.54.0
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATZ
GNOME PPP: STDERR: ATZ
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DT8177784037
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT8177784037
GNOME PPP: STDERR: CONNECT 460800
GNOME PPP: STDERR: --> Carrier detected.  Waiting for prompt.
GNOME PPP: STDERR: Level 3 Comm nas163.dal1 UQKT2
GNOME PPP: STDERR: Username:/login:/Login:
GNOME PPP: STDERR: Username:/login:/Login:
GNOME PPP: STDERR: Username:/login:/Login:
GNOME PPP: STDERR: Username:/login:/Login:
GNOME PPP: STDERR: Username:/login:/Login:
GNOME PPP: STDERR: Username:/login:/Login:
GNOME PPP: STDERR: Username:/login:/Login:
GNOME PPP: STDERR: Username:/login:/Login:
GNOME PPP: STDERR: Username:/login:/Login:
GNOME PPP: STDERR: --> Looks like a login prompt.
GNOME PPP: STDERR: --> Sending: (my real username)
GNOME PPP: STDERR: (my real username)
GNOME PPP: STDERR: Password:
GNOME PPP: STDERR: --> Looks like a password prompt.
GNOME PPP: STDERR: --> Sending: (password)
GNOME PPP: STDERR:     Entering PPP Session.
GNOME PPP: STDERR:     IP address is 4.252.248.70
GNOME PPP: STDERR:     MTU is 1524.
GNOME PPP: STDERR: --> Looks like a welcome message.
GNOME PPP: STDERR: --> Starting pppd at Sun Nov  6 18:14:47 2005
GNOME PPP: STDERR: --> pid of pppd: 8974
GNOME PPP: STDERR: --> Using interface ppp0
GNOME PPP: STDERR: --> Disconnecting at Sun Nov  6 18:15:16 2005
GNOME PPP: STDERR: --> The PPP daemon has died: A modem hung up the phone (exit code = 16)
GNOME PPP: STDERR: --> man pppd explains pppd error codes in more detail.
GNOME PPP: STDERR: --> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
```


Let me know your thoughts plz :D.

---

### Post by John.Michael.Kane on 2005-11-06
[https://wiki.ubuntu.com/SettingUpModems?highlight=%28modem%29](https://wiki.ubuntu.com/SettingUpModems?highlight=%28modem%29)
[https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28dsl%29](https://wiki.ubuntu.com/ADSLPPPoE?highlight=%28dsl%29)

---

### Post by CameronCalver on 2006-05-11
Hey can someone help me i have a external modem using gnome ppp and it connects to intenret then drops this is what it has to say

Gnomepp stderr ppp negotiation started
"" "" starting ppd at thurday may 11 17:58:00 2006
"" "" pid of pppd:8776
"" "" pppd:z
"" "" using internface ppp0
"" "" ppd:z
"" "" ppd:z
"" "" ppd:z
"" "" ppd:z
"" "" ppd:z
"" "" ppd:z
"" "" disconecting at thur may..........
"" "" the ppp daeman has died:authentication error
"" "" we failed to athenticate ourselves to the perr
"" "" mabe nad account or password (exit code:19)
"" "" man ppd explans pppd error codes in more detail
"" "" i gues thats it for now,exiting
"" "" the ppp daeman has died (exit code = 19

---

