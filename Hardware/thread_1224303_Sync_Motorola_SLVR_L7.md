---
title: "Sync Motorola SLVR L7"
date: 2009-07-27
forum: Hardware
---

### Post by bonzi on 2009-07-27
I have a motorola slvr l7 I want to sync my phone book and sms with ubuntu. Is there any app that does it? I saw wammu (Gammu) does it and supports l7 but I have problems configuring it. Can anyone help me? Even motorola phone tools with wine is ok for me.

---

### Post by bonzi on 2009-07-27
I'm including the wammu log. There seems some problem

```



--------------- System information ----------------
Platform     linux2
Python       2.6.2
wxPython     2.8.9.1
Wammu        0.29
python-gammu 0.28
Gammu        1.22.1
Bluetooth    PyBluez
locales      en_IN (ISO8859-1)
connection   at115200
device       /dev/ttyUSB0
model        auto
Mon 2009/07/27 19:18:05: [Gammu            - 1.22.1 built 17:44:42 Dec 22 2008 using GCC 4.3]
Mon 2009/07/27 19:18:05: [Connection       - "blueat"]
Mon 2009/07/27 19:18:05: [Connection index - 0]
Mon 2009/07/27 19:18:05: [Model type       - ""]
Mon 2009/07/27 19:18:05: [Device           - "00:17:00:68:47:E3"]
Mon 2009/07/27 19:18:05: [Runing on        - Linux, kernel 2.6.28-13-generic (#44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009)]
Mon 2009/07/27 19:18:05: Looking for suitable channel for AT
Mon 2009/07/27 19:18:05: Device 00:17:00:68:47:E3 ("&#946;&#937;nz&#915;")
Mon 2009/07/27 19:18:09:    Channel 1 - "&#2337;&#2366;&#2351;&#2354;-&#2309;&#2346; &#2344;&#2375;" (score=0)
Mon 2009/07/27 19:18:09:    Channel 3 - "&#2357;&#2377;&#2351;&#2360; " (score=0)
Mon 2009/07/27 19:18:09:    Channel 7 - "&#2361;&#2376;&#2306;&#2337;&#2360;&#2381;&#2347;" (score=0)
Mon 2009/07/27 19:18:09:    Channel 8 - "OBEX &#2321;&#2348;&#2332;&#2375;" (score=0)
Mon 2009/07/27 19:18:09:    Channel 9 - "OBEX &#2398;&#2366;&#2311;&#2354; &#2360;" (score=0)
Mon 2009/07/27 19:18:09:    Channel 10 - "&#2311;&#2350;&#2375;" (score=0)
Mon 2009/07/27 19:18:09: No suitable bluetooth channel found!
Mon 2009/07/27 19:18:09: Init:GSM_TryGetModel failed with error NOTSUPPORTED[21]: Function not supported by phone.
Mon 2009/07/27 19:18:09: [Gammu            - 1.22.1 built 17:44:42 Dec 22 2008 using GCC 4.3]
Mon 2009/07/27 19:18:09: [Connection       - "blueobex"]
Mon 2009/07/27 19:18:09: [Connection index - 0]
Mon 2009/07/27 19:18:09: [Model type       - ""]
Mon 2009/07/27 19:18:09: [Device           - "00:17:00:68:47:E3"]
Mon 2009/07/27 19:18:09: [Runing on        - Linux, kernel 2.6.28-13-generic (#44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009)]
Mon 2009/07/27 19:18:09: Looking for suitable channel for OBEX
Mon 2009/07/27 19:18:09: Device 00:17:00:68:47:E3 ("&#946;&#937;nz&#915;")
Mon 2009/07/27 19:18:11:    Channel 1 - "&#2337;&#2366;&#2351;&#2354;-&#2309;&#2346; &#2344;&#2375;" (score=0)
Mon 2009/07/27 19:18:11:    Channel 3 - "&#2357;&#2377;&#2351;&#2360; " (score=0)
Mon 2009/07/27 19:18:11:    Channel 7 - "&#2361;&#2376;&#2306;&#2337;&#2360;&#2381;&#2347;" (score=0)
Mon 2009/07/27 19:18:11:    Channel 8 - "OBEX &#2321;&#2348;&#2332;&#2375;" (score=1)
Mon 2009/07/27 19:18:11:    Channel 9 - "OBEX &#2398;&#2366;&#2311;&#2354; &#2360;" (score=1)
Mon 2009/07/27 19:18:11:    Channel 10 - "&#2311;&#2350;&#2375;" (score=0)
Mon 2009/07/27 19:18:11: Connecting to RF channel 8
Mon 2009/07/27 19:18:11: [Module           - "auto"]
Mon 2009/07/27 19:18:11: Connected using model 
Mon 2009/07/27 19:18:11: Folder Browsing service requested
Mon 2009/07/27 19:18:11: Connecting
Mon 2009/07/27 19:18:11: SENDING frametype 0x80/length 0x17/23
Mon 2009/07/27 19:18:11: 10 |00 |04 |00 |46F|00 |13 |F9 |EC |7B{|C4 |95 |3C<|11 |D2 |98  ....F....{..<...
Mon 2009/07/27 19:18:11: 4EN|52R|54T|00 |DC |9E |09                                      NRT....         
Mon 2009/07/27 19:18:11: RECEIVED frametype 0xC3/length 0x04/4
Mon 2009/07/27 19:18:11: 10 |00 |14 |06                                                  ....            
Mon 2009/07/27 19:18:11: Connection not allowed!
Mon 2009/07/27 19:18:11: Disconnecting
Mon 2009/07/27 19:18:11: SENDING frametype 0x81/length 0x00/0
Mon 2009/07/27 19:18:12: RECEIVED frametype 0xC0/length 0x00/0
Mon 2009/07/27 19:18:12: Wrong request sent to phone!
Mon 2009/07/27 19:18:12: Init:GSM_TryGetModel failed with error NOTSUPPORTED[21]: Function not supported by phone.
Mon 2009/07/27 19:18:12: Entering GSM_SetIncomingSMS
Mon 2009/07/27 19:18:12: GSM_SetIncomingSMS failed with error NOTIMPLEMENTED[25]: Function not implemented. Help required.
Mon 2009/07/27 19:18:12: Leaving GSM_SetIncomingSMS
Mon 2009/07/27 19:18:12: Entering GSM_SetIncomingCall
Mon 2009/07/27 19:18:12: GSM_SetIncomingCall failed with error NOTIMPLEMENTED[25]: Function not implemented. Help required.
Mon 2009/07/27 19:18:12: Leaving GSM_SetIncomingCall
Mon 2009/07/27 19:18:12: Entering GSM_SetIncomingCB
Mon 2009/07/27 19:18:12: GSM_SetIncomingCB failed with error NOTIMPLEMENTED[25]: Function not implemented. Help required.
Mon 2009/07/27 19:18:12: Leaving GSM_SetIncomingCB
Mon 2009/07/27 19:18:12: Entering GSM_SetIncomingUSSD
Mon 2009/07/27 19:18:12: GSM_SetIncomingUSSD failed with error NOTIMPLEMENTED[25]: Function not implemented. Help required.
Mon 2009/07/27 19:18:12: Leaving GSM_SetIncomingUSSD
Mon 2009/07/27 19:18:12: [Terminating]
Mon 2009/07/27 19:18:12: Disconnecting
Mon 2009/07/27 19:18:12: SENDING frametype 0x81/length 0x00/0
Mon 2009/07/27 19:18:12: RECEIVED frametype 0xC0/length 0x00/0
Mon 2009/07/27 19:18:12: Wrong request sent to phone!
Mon 2009/07/27 19:18:12: [Gammu            - 1.22.1 built 17:44:42 Dec 22 2008 using GCC 4.3]
Mon 2009/07/27 19:18:12: [Connection       - "bluerfgnapbus"]
Mon 2009/07/27 19:18:12: [Connection index - 0]
Mon 2009/07/27 19:18:12: [Model type       - ""]
Mon 2009/07/27 19:18:12: [Device           - "00:17:00:68:47:E3"]
Mon 2009/07/27 19:18:12: [Runing on        - Linux, kernel 2.6.28-13-generic (#44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009)]
Mon 2009/07/27 19:18:12: Using hard coded bluetooth channel 14.
Mon 2009/07/27 19:18:12: Connecting to RF channel 14
Mon 2009/07/27 19:18:12: Can't connect (111, Connection refused)
Mon 2009/07/27 19:18:12: Init:GSM_TryGetModel failed with error DEVICEOPENERROR[2]: Error opening device. Unknown/busy or no permissions.


```

---

### Post by bonzi on 2009-07-31
Any help or any alternative solution???

---

