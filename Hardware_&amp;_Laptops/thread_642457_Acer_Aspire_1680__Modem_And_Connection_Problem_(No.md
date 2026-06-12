---
title: "Acer Aspire 1680 | Modem And Connection Problem (No Dial Tone)"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by mohajerx on 2007-12-16
Hello ,
**Modem : SoftV92 Data Fax with smartCP**
I use Dialup.
I can not connect to internet via ubuntu
or with network enable i can use internet in ubuntu.

modem installed and wvdialconf can confirm modem.
i use Wvdial & pppconfig to connect but still not connected.

i set modem port and internet connection details in both wvdial file and pppconfig , and also in Network >> Modem Option

There is no problem from Phone Line to Modem ,
Phone line is connected to modem.

[SIZE=4]Wvdial Config :[/SIZE]
Found a modem on /dev/**ttySL0**.
Modem configuration written to /etc/wvdial.conf.
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem

[SIZE=4]After Wvdial Command:[/SIZE]
mohajer:~$ wvdial
WvDial<*1>: WvDial: Internet dialer version 1.56
WvModem<*1>: Cannot get information for serial port.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT9712264
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT9712264
WvDial Modem<*1>: [SIZE=3]**NO DIALTONE**[/SIZE]
WvDial<Err>: **No dial tone**.


[SIZE=4]Plog :
[/SIZE]Dec 10 18:32:12 mohajer-laptop chat[5839]:  -- got it 
Dec 10 18:32:12 mohajer-laptop chat[5839]: send (ATDT9712254^M)
Dec 10 18:32:12 mohajer-laptop chat[5839]: expect (CONNECT)
Dec 10 18:32:12 mohajer-laptop chat[5839]: ^M
Dec 10 18:32:12 mohajer-laptop chat[5839]: ATDT9712254^M^M
Dec 10 18:32:15 mohajer-laptop chat[5839]: NO DIALTONE
Dec 10 18:32:15 mohajer-laptop chat[5839]:  -- failed
Dec 10 18:32:15 mohajer-laptop chat[5839]: Failed (NO DIALTONE)
Dec 10 18:32:15 mohajer-laptop pppd[5837]: Connect script failed
Dec 10 18:32:16 mohajer-laptop pppd[5837]: Exit.



[SIZE=4]/var/messages/
[/SIZE]Dec 10 18:38:55 mohajer-laptop pppd[6221]: pppd 2.4.4 started by root, uid 0
Dec 10 18:38:56 mohajer-laptop chat[6223]: abort on (BUSY)
Dec 10 18:38:56 mohajer-laptop chat[6223]: abort on (NO CARRIER)
Dec 10 18:38:56 mohajer-laptop chat[6223]: abort on (VOICE)
Dec 10 18:38:56 mohajer-laptop chat[6223]: abort on (NO DIALTONE)
Dec 10 18:38:56 mohajer-laptop chat[6223]: abort on (NO DIAL TONE)
Dec 10 18:38:56 mohajer-laptop chat[6223]: abort on (NO ANSWER)
Dec 10 18:38:56 mohajer-laptop chat[6223]: abort on (DELAYED)
Dec 10 18:38:56 mohajer-laptop chat[6223]: send (ATZ^M)
Dec 10 18:38:56 mohajer-laptop chat[6223]: expect (OK)
Dec 10 18:38:56 mohajer-laptop chat[6223]: ATZ^M^M
Dec 10 18:38:56 mohajer-laptop chat[6223]: OK
Dec 10 18:38:56 mohajer-laptop chat[6223]:  -- got it 
Dec 10 18:38:56 mohajer-laptop chat[6223]: send (ATDT9712254^M)
Dec 10 18:38:57 mohajer-laptop chat[6223]: expect (CONNECT)
Dec 10 18:38:57 mohajer-laptop chat[6223]: ^M
Dec 10 18:38:57 mohajer-laptop chat[6223]: ATDT9712254^M^M
Dec 10 18:39:00 mohajer-laptop chat[6223]: NO DIALTONE
Dec 10 18:39:00 mohajer-laptop chat[6223]:  -- failed
Dec 10 18:39:00 mohajer-laptop chat[6223]: Failed (NO DIALTONE)
Dec 10 18:39:01 mohajer-laptop pppd[6221]: Exit
[B]
egrep -v '#|^ *$' /etc/ppp/options[/B]
mohajer@mohajer:~$ egrep -v '#|^ *$' /etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

[B]Another Plog :
[/B]Dec 16 22:58:05 mohajer chat[6270]: AT&FH0L3^M^M
Dec 16 22:58:05 mohajer chat[6270]: OK^M
Dec 16 22:58:05 mohajer chat[6270]: ATDT97126752^M^M
Dec 16 22:58:08 mohajer pppd[6273]: pppd 2.4.4 started by root, uid 0
Dec 16 22:58:08 mohajer pppd[6273]: **Device ttySL0 is locked by pid 6167**
Dec 16 22:58:08 mohajer pppd[6273]: Exit.
Dec 16 22:58:08 mohajer chat[6270]: NO DIALTONE
Dec 16 22:58:08 mohajer chat[6270]:  -- failed
Dec 16 22:58:08 mohajer chat[6270]: Failed (NO DIALTONE)
Dec 16 22:58:08 mohajer pppd[6167]: Connect script failed
mohajer@mohajer

---

### Post by mohajerx on 2007-12-17
any suggestion ?

---

### Post by mohajerx on 2007-12-21
not work yet. no dial tone.

---

