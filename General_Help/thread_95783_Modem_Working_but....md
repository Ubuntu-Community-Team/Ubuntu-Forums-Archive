---
title: "Modem Working but..."
date: 2005-11-27
forum: General Help
---

### Post by stalflare on 2005-11-27
Hi everyone I am new to Ubuntu and probably the followquestion will appear rather stupid...

I have installed the OS ok, and it detects my modem as a standard "MODEM". I did an autoconfig, put all the telephone numbers and passwords and when I "activate" it it conncects to the ISP no problem. 
So I was waiting for some sort of icon to appear, just to notify that the connection is working, but nothing happened. 
I tried browsing with FFox but no chance there either... Still the modem seems connected, it did make all those strange noises that dialup modems normally do..

Am I doning something wrong? Surely there are some passages that I am missing somewhere...

Can anyone help ?

Thanks a lot!

---

### Post by 23meg on 2005-11-27
Make sure your modem connection is selected as the "default gateway" in System / Administration / Networking.

---

### Post by Bachstelze on 2005-11-27
The classic problem of a DNS misconfiguration... Can you connect to your ISP from a windows machine ? If so, open a command line (Start > Run > cmd) and type "ipconfig -a". Then search for a "Primary DNS" line with an IP address and note it somewhere. Back on ubuntu, run the network-admin, go to the DNS tab, click to add a DNS server and type the IP we found on windows. Click OK, now you should be able to browse the web :) But you could save the hassle and connect through wvdial, it configures the DNS automatically (at least it did for me)


@23meg > my modem works fine, even though it is not selected as default gateway device.

---

### Post by stalflare on 2005-11-27
Hi Hymn and 23meg

I have tried what you were suggesting but the Windows command appear to be "ipconfig /all" and on the "Primary Dns Suffix" tab there is a fat NOTHING... :(

So I am going to try with the DNS servers that are listed below... 

How does this wvdial work? Is it a packet that I have to install?

As fot the default gateway I am going to make sure that it's set properly...

---

### Post by Bachstelze on 2005-11-27
[QUOTE=stalflare]How does this wvdial work? Is it a packet that I have to install?[/QUOTE]

No, it's installed with Ubuntu. Just to see if your modem works fine, try running

```
sudo wvdialconf /etc/wvdial.conf
```

---

### Post by stalflare on 2005-11-28
I have tried running the command and everything seems ok, he gives a bunch of stats and tells me the maximum transfer capability etrc etc...

I still can't configure the "default gateway" option under "admin ---> network", it seems that the modem is ok but the rest doesn't want to see it... :(

These are the results:

udo wvdialconf /etc/wvdial.conf

ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0
<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0
<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0
<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0
<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0
<*1>: Modem Identifier: ATI -- 56000
ttyS0
<*1>: Speed 4800: AT -- OK
ttyS0
<*1>: Speed 9600: AT -- OK
ttyS0
<*1>: Speed 19200: AT -- OK
ttyS0
<*1>: Speed 38400: AT -- OK
ttyS0
<*1>: Speed 57600: AT -- OK
ttyS0
<*1>: Speed 115200: AT -- OK
ttyS
<*1>: Max speed is 115200; that should be safe.
ttyS0
<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS1
<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1
<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1
<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan
<*1>: S2   S3   S4   S5   S6   S7   S8   S9
Port Scan
<*1>: S10  S11  S12  S13  S14  S15  S16  S17
Port Scan
<*1>: S18  S19  S20  S21  S22  S23  S24  S25
Port Scan
<*1>: S26  S27  S28  S29  S30  S31  S32  S33
Port Scan
<*1>: S34  S35  S36  S37  S38  S39  S40  S41
Port Scan
<*1>: S42  S43  S44  S45  S46  S47  S48  S49
Port Scan
<*1>: S50  S51  S52  S53

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.cong.
ttyS0
<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

---

### Post by Bachstelze on 2005-11-28
now try to run

```
sudo gedit /etc/wvdial.conf
```

and edit the last three lines with your ISPs informations. Do not forget to remove the semiolons at the beginning of those lines. Then Save your file wand try to run

```
sudo wvdial
```

---

### Post by stalflare on 2005-11-29
Sorry Hymn just to make clear, the ISP informations are the DNS addresses that i got from windows?

---

### Post by sunny_nwho on 2005-11-29
I did what was suggested in this post and I get the following does this mean my modem is working

sunny@sunbuntu:~$ sudo wvdialconf /etc/wvdial.conf
Password:
Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47  S48
Port Scan<*1>: S49  S50  S51  S52  S53
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

i have not yet checked with a telephone line plugged in....

---

### Post by Bachstelze on 2005-11-29
@stalflare > If i'm not mistaken, the three last lines in the /etc/wvdial.conf file are your ISPs phone " and your login informations.

@sunny > try doing the same thing, it should work fine.

---

### Post by sunny_nwho on 2005-12-01
Actually i am a newbie....I would suggest installing gnome ppp and try it iwll solve the probelm of dialing provided u have ur modem detected....Sunny

---

### Post by akiro.yamamoto on 2005-12-01
Or you can try the built in gnome modem monitor and network monitor....
Right click on the top gnome panel >>  add to panel ...
Then select modem monitor and you can use that for a nice gui modem set up...  I would also do the same process and add the Network monitor....
That prog will give you a visual cue when your connection is successful..
Hope this helps..
Regards

---

### Post by stalflare on 2005-12-22
[QUOTE=HymnToLife]now try to run

```
sudo gedit /etc/wvdial.conf
```

and edit the last three lines with your ISPs informations. Do not forget to remove the semiolons at the beginning of those lines. Then Save your file wand try to run

```
sudo wvdial
```[/QUOTE]


Hymn,

sorry for the late reply but I have had a cruciate ligament surgery and wasn-t able to connect for some time... I have tried the thing above and IT WORKS!!!
Does it means that in order to use the modem I have to run that command every time from the terminal_? Or is there a quicker way?

---

