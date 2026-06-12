---
title: "Problems with dial-up modem on Dell Laptop"
date: 2009-04-06
forum: Hardware
---

### Post by aryangor on 2009-04-06
Hey all!

I am using Intrepid with KDE4.1. I've got it on Dell E6400 laptop, that contains a built-in modem. This modem uses sim cards. So I put in my sim and try to use wvdial but I get the annoying:

"Disconnecting...
The PPP daemon has died: A modem hung up the phone (exit code = 16)
man pppd explains pppd error codes in more detail.
Try again and look into /var/log/messages and the wvdial and pppd man pages for more information."

I naturally ran
ABC@ABC:~$ sudo wvdialconf /etc/wvdial.conf
then
ABC@ABC:~$ sudo kate /etc/wvdial.conf
and edited that. The error appears on typing
ABC@ABC:~$ sudo wvdial hsdpa

I thought that there could be a problem with my sim, but I tested it in another PC's external dial-up modem, and it works. It also works in Windows. Basically it works everywhere except where its supposed to! :( So I suspect that my modem hardware isn't configured properly in Intrepid.

I searched countless posts and tried many solutions. Only one solution worked - I actually WAS online + downloaded some stuff through apt-get! But after I rebooted, its back to non-working and I havent got a clue what can cause this error.

In the future I would like to utilize gnome-ppp or kppp to connect, but now its just back to basics...

I am using "Vodacom South Africa" network. I posted my modem settings below - if you need any other info, I will provide it.

**** /etc/wvdial.conf ****

[Dialer Defaults]
Init1 = ATH     #ATZ gives an error
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
ISDN = 0
New PPPD = yes
Dial Command = ATDT
Carrier Check = no
Auto Reconnect = off

[Dialer hsdpa]
#Init3 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#Init4 string is the one that made modem work once - maybe the word
#"internet" should be something else?
Init4 = AT+CGDCONT=1,"IP","internet"
Stupid Mode = 1
Modem = /dev/ttyACM0
Modem Type = Analog Modem
Baud = 460800
Phone = *99***1#
Username = simobil
Password = none
*********************

---

### Post by aryangor on 2009-04-07
Hellooo? Is anyone there? Please, people, I need your help - any suggestion will be appreciated. ):P

---

### Post by GeorgeVita on 2009-04-07
Hi **aryangor**,

Please post the output of terminal commands:
**ls /dev/ttyU* /dev/ttyA***
**lsusb**

regards,
George

---

### Post by aryangor on 2009-04-07
> **GeorgeVita said:**
> Hi **aryangor**,

Please post the output of terminal commands:
**ls /dev/ttyU* /dev/ttyA***
**lsusb**

regards,
George

********************
**ABC@ABC:~$ ls -l /dev/ttyU* /dev/ttyA***
ls: cannot access /dev/ttyU*: No such file or directory
crw-rw---- 1 root dialout 166, 0 2009-04-07 12:54 /dev/ttyACM0
crw-rw---- 1 root dialout 166, 1 2009-04-07 12:54 /dev/ttyACM1
crw-rw---- 1 root dialout 166, 2 2009-04-07 12:54 /dev/ttyACM2
********************
**ABC@ABC:~$ lsusb**
Bus 008 Device 002: ID 413c:8147 Dell Computer Corp.
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0c45:63f8 Microdia
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0a5c:5800 Broadcom Corp.
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 413c:8156 Dell Computer Corp.
Bus 001 Device 005: ID 413c:8158 Dell Computer Corp.
Bus 001 Device 004: ID 413c:8157 Dell Computer Corp.
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp.
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
***************

Thanx!

---

### Post by GeorgeVita on 2009-04-07
> **aryangor said:**
> ...
Bus 008 Device 002: ID 413c:8147 Dell Computer Corp.
...


There is a definition for the above inside HAL information file:
/usr/share/hal/fdi/information/10freedesktop/10-modem.fdi

Have you tried setup a Mobile Broadband connection via Network Manager (N.M.) icon?
(right click 2PC screens, Edit Connections, Mobile Broadband, Add, choose country and provider..)

At N.M. Vodacom South Africa has 2 APN options: **internet** and **unrestricted** whith Phone=***99#** (both)

EDIT: If Network Manager does not work, try wvdial with **modem=/dev/ttyACM1** (at /etc/wvdial.conf)
......in any error post all the output of wvdial

G

---

### Post by aryangor on 2009-04-07
> **GeorgeVita said:**
> 

EDIT: If Network Manager does not work, try wvdial with **modem=/dev/ttyACM1** (at /etc/wvdial.conf)
......in any error post all the output of wvdial

G

I don't have network-manager-kde any more, I removed it some time ago. I am trying to reinstal it bach from the CD, but apt-get says there are unmet dependencies, so I will migrate between WinXP and Ibex copying packages until I got N.M. up and running.

Meanwhile I tried the stuff as quoted above - but no success. Below is the **wvdial** output:

********************
**ABC@ABC:~$ sudo wvdial hsdpa**
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATH
ATH
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Sending: AT+CGDCONT=1,"IP","unrestricted"
AT+CGDCONT=1,"IP","unrestricted"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&&,,#|f~
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Apr  7 14:57:59 2009
--> Pid of pppd: 9809
--> Using interface ppp0
--> Disconnecting at Tue Apr  7 14:58:00 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
********************

Exactly the same appears in the LOG of gnome-ppp btw.

---

### Post by GeorgeVita on 2009-04-07
> **aryangor said:**
> ...
**ABC@ABC:~$ sudo wvdial hsdpa**
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATH
ATH
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2
ATQ0 V1 E1 S0=0 &C1 &D2
OK
--> Sending: AT+CGDCONT=1,"IP","unrestricted"
AT+CGDCONT=1,"IP","unrestricted"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&&,,#|f~
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Tue Apr  7 14:57:59 2009
[COLOR="YellowGreen"][B]--> Pid of pppd: 9809
--> Using interface ppp0
[/B][/COLOR]--> Disconnecting at Tue Apr  7 14:58:00 2009
...


It seems to connected ok, but the provider does not supply IP adress and DNS and **disconnects you**.
If you tried the above with /dev/ttyUSB0 and /dev/ttyUSB1 with both APN options (internet/unrestricted) then we have a problem!

As you can connect with this SIM via windows (you noticed in your 1st post) can you enable (in windows) the modem log file through control panel, modem & dialling, advanced properties. After connecting read this file to determine init string (AT commands) and possibly the APN setting (AT+CGDCONT=1,...). The dial no is hidden (****) but with the number of stars we can imagine it!

Waiting for new data,
G

EDIT: searching for **413c:8147** and **linux** I found: [http://www.natisbad.org/E4300/index.html](http://www.natisbad.org/E4300/index.html)

---

### Post by aryangor on 2009-04-07
YES - WE DID IT!!!

I looked into the modem log in WinXP and managed to extract the Init strings. There was no Init for "AT+CGDCONT=1,..." but I found that AT and AT&F were present. Not sure about AT, but AT&F resets the device to factory-defined configuration. ATH, on the other hand, signals the modem to terminate an active call - and I had it all along!! Thats why it ran only once - after the first run the configurations were changed and needed to be reset again with AT&F.

*************************

[Dialer Defaults]
[B]Init1 = AT
Init2 = AT&F[/B]
New PPPD = yes
Dial Command = ATDT
ISDN = 0
Carrier Check = no
Auto Reconnect = off

[Dialer hsdpa]
Init3 = AT&F V1 E0 X1 S0=0 &C1 &D2 +FCLASS=0
Init4 = AT S7=60; +DS=3,0,2048,32
Stupid Mode = 1
Modem Type = Analog Modem
Phone = *99#
Modem = /dev/ttyACM1
Username = simobil
Password = none
Baud = 460800

***************************

If you would not give that web-link earlier, I would not be able to understand the definitions of each string and hence figure out the problem. Thanx a million, G! Efharisto!! :lolflag:

---

