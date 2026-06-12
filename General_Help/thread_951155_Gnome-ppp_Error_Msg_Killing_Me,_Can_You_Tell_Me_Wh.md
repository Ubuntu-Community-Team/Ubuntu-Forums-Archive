---
title: "Gnome-ppp Error Msg Killing Me, Can You Tell Me What That Error Mean?"
date: 2008-10-17
forum: General Help
---

### Post by eAi-T0ky0 on 2008-10-17
I have some problems with my USB Huawei e220 My problem is I´ve configured several times /etc/wvdial.conf I almost get modem connected but I always get an error in idle time that doesn´t let me contiune.


--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","pps";
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Oct 18 00:25:18 2008
--> Pid of pppd: 6215
--> Disconnecting at Sat Oct 18 00:25:19 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)


I´ll really appreciate if you can guide me, last time with Debian in my PC I got my modem ready, but now I can´t.

---

### Post by niteshifter on 2008-10-17
Hi,

Something is not configured correctly. Look in /var/log/messages to see what pppd is actually complaining about. If you like post your wvdial.conf and the lines in /var/log/messages after pppd starts. 

For example, I'll give a section of my /var/log/messages when I've connected via USB modem (cell phone in this case):
```
Oct 17 20:12:46 dell-desktop pppd[6473]: pppd 2.4.4 started by root, uid 0
Oct 17 20:12:46 dell-desktop kernel: [  115.008000] PPP generic driver version 2.4.2
Oct 17 20:12:46 dell-desktop pppd[6473]: Using interface ppp0
Oct 17 20:12:46 dell-desktop pppd[6473]: Connect: ppp0 <--> /dev/ttyACM0
Oct 17 20:12:46 dell-desktop pppd[6473]: PAP authentication succeeded
Oct 17 20:12:46 dell-desktop kernel: [  115.164000] PPP BSD Compression module registered
Oct 17 20:12:46 dell-desktop kernel: [  115.232000] PPP Deflate Compression module registered
Oct 17 20:12:49 dell-desktop pppd[6473]: local  IP address 166.214.128.6
Oct 17 20:12:49 dell-desktop pppd[6473]: remote IP address 192.168.100.101
Oct 17 20:12:49 dell-desktop pppd[6473]: primary   DNS address 209.183.35.23
Oct 17 20:12:49 dell-desktop pppd[6473]: secondary DNS address 209.183.33.23
Oct 17 20:13:06 dell-desktop kernel: [  135.088000]          res 40/00:24:3f:1b:c5/00:00:09:00:00/40 Emask 0x2 (HSM violation)
```
The above shows a successful connect via wvdial.

---

### Post by thiagoikari on 2008-12-19
I am using the Giant D301 modem and I&#7743; getting the exact same error.

Watching the /var/log/messages is no use, it doesnt even move when I try to connect as a normal user.

However if I sudo, it connects perfectly.

Ie had some permitions problems with the pppd but i solved it chmoding it to let everyone execute it.

If anyone knows anything about it... =)

P.S.: Looking in man pppd, it says that the exit code 2 means that there are two conflicting options in pppd.conf

I will check it out later

---

### Post by RJARRRPCGP on 2008-12-19
> **eAi-T0ky0 said:**
> I have some problems with my USB Huawei e220 My problem is I´ve configured several times /etc/wvdial.conf I almost get modem connected but I always get an error in idle time that doesn´t let me contiune.


--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","pps";
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Oct 18 00:25:18 2008
--> Pid of pppd: 6215
--> Disconnecting at Sat Oct 18 00:25:19 2008
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)


I´ll really appreciate if you can guide me, last time with Debian in my PC I got my modem ready, but now I can´t.

I had the same type of problem when I used to have POTS, which was before May 17, 2007, but with KPPP, I ALWAYS got disconnected pronto, ALWAYS hangs up pronto! It acts like if I hang it up myself right after dialing, except it does it on its own!. It hangs up right after dialing. And get an error message about the PPP daemon dying unexpectedly, equivalent to the Windows "Error The X Y Z service has terminated unexpectedly. It has done this 1 time(s)." (or similar) The only way I could use the internet was to use ```
pppconfig 
``` and ```
pon (ISP name)
```

---

