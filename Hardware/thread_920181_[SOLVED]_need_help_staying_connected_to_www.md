---
title: "[SOLVED] need help staying connected to www"
date: 2008-09-15
forum: Hardware
---

### Post by Ric1501 on 2008-09-15
hello - new to ubuntu, but savy with almost 20 yrs windows (xp,vista,etc) and finally decided to go open source. hit a brickwall though. problem staying connected to web via broadband usb modem. can only stay connected 2.5 mins, then disconnected. currently using gnome ppp to reconnect every 2.5 mins. need help to stay connected. would love to stay with ubuntu, it is fast, no problems diving in blind and seeing the light. running hardy 8.04 latest, trying to upd, but here is where the wall came tumbling down hard due to connection problem using usb razr vm3. yes, it is recognized, I am on it now, just drops connection...

sudo wvdialconf wvtest
ttyUSB0<*1>: Modem Identifier: ATI -- Manufacturer: I: Motorola CE, Copyright 20
modem on /dev/ttyUSB0
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0

Modem type: 		Motorola USB Modem 
Modem inf path: 	oem3.inf 
Modem inf section: 	USB1XCDMA 
Matching hardware ID: 	usb\vid_22b8&pid_2a64&mi_00 
			230400,8,N,1, ctsfl=0, rtsctl=1 
			115200,8,N,1, ctsfl=1, rtsctl=2 

here is my wvdial.conf

[Dialer Defaults]
    modem=/dev/ttyUSB0
    baud=115200,8,N,1
    ctsfl=1
    rtsctl=2 
    init1=ATZ
    init2=ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
    ISDN = 0
    modem type=USB Modem
    phone=#777
    username=''
    password=''
    stupid mode=yes
    lcp-echo-interva=30 
    lcp-echo-failure=4 
    noipx

it does connect -------------

r@ub1501:~$ sudo wvdial
--> Ignoring malformed input line: "    noipx"
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT#777
--> Waiting for carrier.
ATDT#777
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sun Sep 14 22:49:12 2008
--> Pid of pppd: 10281
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533;&#65533;[08]&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;&#65533;&#65533;[08]&#65533;[06][08]&#65533;&#65533;[06][08]
--> pppd: &#65533;&#65533;&#65533;&#65533;[08]&#65533;[06][08]&#65533;&#65533;[06][08]
--> local  IP address 
--> pppd: &#65533;&#65533;&#65533;&#65533;[08]&#65533;[06][08]&#65533;&#65533;[06][08]
--> remote IP address 
--> pppd: &#65533;&#65533;&#65533;&#65533;[08]&#65533;[06][08]&#65533;&#65533;[06][08]
--> primary   DNS address 
--> pppd: &#65533;&#65533;&#65533;&#65533;[08]&#65533;[06][08]&#65533;&#65533;[06][08]
--> secondary DNS address 
--> pppd: &#65533;&#65533;&#65533;&#65533;[08]&#65533;[06][08]&#65533;&#65533;[06][08]

--> Disconnecting at Sun Sep 14 22:51:43 2008
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded(often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)

but disconnects as you have read. been searching for solutions, lots of configs but no solution. any advice or fix grants many thanks from me in advance ..

---

### Post by knattlhuber on 2008-09-15
What if you set these to zero:

```
...
lcp-echo-interva=30
lcp-echo-failure=4
...
```

---

### Post by Ric1501 on 2008-09-15
no such luck. seems hardy loads multiple USB OHCI controllers and hub interfaces, not the actual drivers that are need to run Dell components. does not recognize my usb at startup, have to manually load via CL my usb ven and prd id. forgot to mention this is loaded on a laptop 1501, 8g ram, 320 hdd, amd sempron. think all pkgs have been upd, took many hrs and to many 2.5 min connects. somebody has to have a fix for this - cannot be the only one to have this problem. still smiling though tired of racing the connect button for www access ....

---

### Post by knattlhuber on 2008-09-15
That would have been too good to be true...
Could it be that there is another conf file (e.g. in /etc/ppp or its subfolders) whose settings override those from wvdial.conf? To test this, you could change

```
lcp-echo-interval=30
lcp-echo-failure=4 
```

in wvdial.conf to an interval of, say, 60. That should keep you connected for (4 + 1) * 60 seconds (testing 4 times after every 60 seconds before it drops the connection). If things don't change, we are probably modifying the wrong conf file for this connection. I know that this is a very pedestrian way to tackle this problem, but, hey, desperate times, desperate measures.
Also, I noticed that an 'l' is missing here. Not sure if that matters at all:
```
lcp-echo-interva=30 
```

I hope you are otherwise enjoying Ubuntu/Linux! Stick with it, it's really worth it.

---

### Post by Ric1501 on 2008-09-16
all - jus installed kppp and all, but still having a 2.5 min session before disconnect

also, after kernel auto upd from 16 to 19, my mouse disappears and display locks up -
anyone with any suggestions

many kudos in advance !

---

### Post by IntuitiveNipple on 2008-09-16
Add the **debug** option to the configuration (see man pppd for details) and check if there are any more helpful messages in /var/log/syslog.

make sure you have corrected the typing mistake that knattlhuber pointed out.

---

### Post by Ric1501 on 2008-09-16
all - jus installed kppp and all, but still having a 2.5 min session before disconnect

also, after kernel auto upd from 16 to 19, my mouse disappears and display locks up -
anyone with any suggestions

many kudos in advance !

---

### Post by Ric1501 on 2008-09-16
thnxs - will do Y to typo

---

### Post by Ric1501 on 2008-09-17
where do i add the cmd > silent in my wvdial.conf file 

or

what should be my wvdial.conf file

according to linux man, using the 'silent' option, pppd will not transmit LCP packets to initiate a  connection until a valid LCP packet is received from the peer

thus my problemo should be resolved, but when i added it - ole PPP daemon ignored my input calling it malformed - who is this guy and how dare he ...

LOL - anyone else with a possibility or solution

ric

---

### Post by Ric1501 on 2008-09-17
to all who assisted thus far, many thanks! thou i received many emails to resolve this issue, it seems I have to clarify my problem. 

yes - have established connection with my razr3 cell phone via usb cable
yes - did -r usbserial, then modprobe usbserial vendor=0x22b8 product=0x2a64
yes - dmesg|grep -i ttyUSB
yes - gedit wvdial.conf 

can get connected to www, but only maintain connection for 2.5 minutes before
--> Connect time 2.5 minutes.
--> Disconnecting at Wed Sep 17 04:17:10 2008
--> The PPP daemon has died: Lack of LCP echo responses (exit code = 15)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> Provider is overloaded (often the case) or line problem.
--> The PPP daemon has died. (exit code = 15)
r@ub1501:~$ sudo wvdial
Y - tried to use kppp but no success
Y - my phone does work correctly. when i reboot and use vista (ultimate), no problem with connection or maintaining it - connects auto during startup
Y - i can see and access my vista part while using ubuntu
N - i cannot see my linux ubuntu while using vista due to different disk formats - ntfs? and ext2/3 i guess ...

so do i continue and try to resolve this problem or just stay with my underdog VU
problem has become too frustrating trying to learn the ubuntu lingo and open source linux, whose flavor of computerized lifestyle i have quickly come to appreciate

Y - i will continue to research this problem and appreciate all incoming suggestions or maybe even a fix but my constant monitoring of the 2.5 min linkage ........

---

### Post by IntuitiveNipple on 2008-09-18
The only place I use pppd is in a WRT54GL router with dd-wrt and I've never had to do anything except configure it with the web interface so my contribution is going to be limited to spotting obvious issues from reading the manual pages and articles about it.

I'll include the contents of the /etc/ppp/options file from the router in case it offers any insights - don't use it as a complete guide to how yours should be since the set-ups are totally different:
```

defaultroute
usepeerdns
pty 'pptp 10.0.0.138 --nolaunchpppd'
mtu 1460
nomppe
noccp
default-asyncmap
nopcomp
noaccomp
novj
nobsdcomp
nodeflate
lcp-echo-interval 0
noipdefault
lock
noauth

```

---

### Post by Ric1501 on 2008-09-18
TJ - thanx for ur words of encouragement as to staying w/ ubuntu (linux) !!!! 

finally figured what went wrong. had to do some reading inside the /etc folders looking for anything out of the ordinary and noticed that my /etc/ppp/peers/wvdial never got updated - thus the lcp echo cmds never ran their circuit - thus mr daemon was correct with his intel  ... hmmmmmmmm - go figure huh

anyways - up and surfing now. thanxs again - ric

---

### Post by knattlhuber on 2008-09-18
That's what I tried to tell you in my second post... :)

Anyways, glad you got it working now. Welcome to Ubuntu!

---

