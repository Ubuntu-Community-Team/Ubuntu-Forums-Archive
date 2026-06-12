---
title: "smart link modem no dial tone"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by lagosm on 2006-06-14
I have a Sony Vaio laptop (VGN A195-EP). Recently, i have decided to replace the fedora distro with the Ubuntu 6.06 for many reasons. I am very satisfied with it, but I have a problem with the modem. I have already configured the modem as *"https://wiki.ubuntu.com/DialupModemHowto->Software modems->Modems supported by ALSA drivers (snd_atiixp_modem, snd_via82xx_modem, snd_intel8x0m)"* says. I have followed all the steps and all seems to work fine. 
When i try to connect to the network with wvdial, i get the following message: ***"No dial tone"***. Note that, i configure the wvdial as the above link says.
Could you please help me in order to solve this problem? Its the only problem that i have with this distro, and the modem issue is very important to me.

Many thanks

---

### Post by loell on 2006-06-14
in other threads wvdial on ubuntu 6.06 doesn't seem to work.
if you have other connections aside from dial-up then ou could install gnomeppp
if there is no other connections, you could try pppconfig instead..
then use pon and poff command..

---

### Post by vespo on 2006-06-14
Hi

This is how I did get my modem to work
[http://www.ubuntuforums.org/showthread.php?t=195016&highlight=vespo](http://www.ubuntuforums.org/showthread.php?t=195016&highlight=vespo)

hope it helps

---

### Post by lagosm on 2006-06-14
[QUOTE=loell]in other threads wvdial on ubuntu 6.06 doesn't seem to work.
if you have other connections aside from dial-up then ou could install gnomeppp
if there is no other connections, you could try pppconfig instead..
then use pon and poff command..[/QUOTE]

I have tried this with gnomeppp and i get the same results (no dial tone). Also, i try pon/poff again with bad results again.

---

### Post by vespo on 2006-06-14
[QUOTE=loell]in other threads wvdial on ubuntu 6.06 doesn't seem to work.
if you have other connections aside from dial-up then ou could install gnomeppp
if there is no other connections, you could try pppconfig instead..
then use pon and poff command..[/QUOTE]

I might most probably be wrong, but I was told once that many gui dialers (but not kppp for example) will use settings in /etc/wvdial.conf.
Anyway, wvdial is working ok here for dapper and I suggest you give it a further try. If you already installed sl-modem-daemon and you post the output of

```
sudo wvdialconf /etc/wvdial.conf
```

and 

```
wvdial YOUR_DIALER
```

I may try to help further

---

### Post by lagosm on 2006-06-15
I have the wvdial.conf configured as following:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Password = xxxxxx
Phone = xxxxxxxxxx
Modem Type = Analog Modem
Stupid Mode = yes
Baud = 115200
New PPPD = yes
Modem = /dev/ttySL0
ISDN = 0
Username = xxxxxx
Carrier Check = no

***Same as if Baud = 460800***

The results are the following:

--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT8962500000
--> Waiting for carrier.
ATDT8962500000
NO DIALTONE
--> No dial tone.
--> Disconnecting at Wed Jun 14 22:20:21 2006

***When i replace the “Init1 = ATZ” with “Init1 = ATX3” i get the following results:***

--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATX3
ATX3
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT8962500000
--> Waiting for carrier.
ATDT8962500000
NO ANSWER
--> No Answer.  Trying again.
--> Sending: ATDT8962500000
--> Waiting for carrier.
ATDT8962500000 


So, its impossible to make the modem works. Is there any other opinion about this issue?

Thanks

---

### Post by vespo on 2006-06-15
Well, at least with ATX3 you get NO ANSWER instead of NO DIALTONE, we've made some progress. Also if wvdial dials correctly, it will take up to 1 minute to establish connection.

A few more things come to mind:

1. Did you try to dial 8962500000 with your normal telephone and listen if you get the fax-type sounds? 
2. Did you try to replace 8962500000 with another number to check if it can dial at all (for example your mobile phone or a friend phone number)?
3. Did you try to run wvdial as root?
4. Did you try to change /dev/ttySL0 to /dev/modem ?
5. It happened to me that I had to retry a few times before getting logged to the ISP, so be patient and retry.
6. Those lines:

```
NO ANSWER
--> No Answer. Trying again.
--> Sending: ATDT8962500000
--> Waiting for carrier.
ATDT8962500000 
```

Are they repeated in a loop or it justs stops there and then it disconnects as without ATX3? If it does not disconnect, wait for at least 1 minute before hitting Ctrl+C.

7. Did you change COUNTRY from USA to YOUR_COUNTRY settings as I suggested?

I would still like to see the output of
```
sudo wvdialconf /etc/wvdial.conf
```

Cheers

---

### Post by lagosm on 2006-06-15
1. yes
2. yes
3. Yes. Usually i run it as root.
4. yes
6. Yes these lines repeated. I had waited more than a minute before hitting Ctrl+C.
7. yes

The output of the sudo wvdialconf /etc/wvdial.conf is the following:

Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   S4   S5   S6   S7
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31
Modem Port Scan<*1>: S32  S33  S34  S35  S36  S37  S38  S39
Modem Port Scan<*1>: S40  S41  S42  S43  S44  S45  S46  S47
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

---

### Post by vespo on 2006-06-16
Ok,

I checked you wvdial.conf against mine and it's the same, except that I pass the X3 init string twice. Like that:

```
[Dialer tele2]
Modem = /dev/ttySL0
Init1 = ATX3
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 X3
Stupid Mode = yes
Modem Type = Analog Modem
Phone = 7020221022
New PPPD = yes
ISDN = 0
Username = tele2internet
Carrier Check = no
Password = tele2internet
Baud = 460800

```

This shouldn't make a big difference.

If you can dial your cell phone as you say, then I think your problem is just to pass the right init strings to your modem so to hook properly to your ISP provider.  I am no AT expert and this matter changes from country to country, you have to try and ask somebody from your country.

You could also try a different ISP as their connection defaults can be different (allowed speed for example, in Italy I always get slightly different max speeds for libero.it and tele2.it, however it never goes to the declared max).

I am sorry I can't be of further help.

Cheers

---

