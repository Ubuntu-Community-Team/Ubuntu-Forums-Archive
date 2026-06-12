---
title: "Problem with bluetooth rfcomm"
date: 2009-10-31
forum: Hardware
---

### Post by oyankee on 2009-10-31
Hi, I used to connect to internet through mobile phone (now N95).

```
sdptool browse 00:1C:D4:47:D1:3C
Browsing 00:1C:D4:47:D1:3C ...
Service Name: AVRCP Target
Service Description: Audio Video Remote Control
Service Provider: Symbian Software Ltd.
Service RecHandle: 0x10000
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: Audio Source
Service RecHandle: 0x10003
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service Name: Hands-Free Audio Gateway
Service RecHandle: 0x10004
Service Class ID List:
  "Handsfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0105

Service Name: Headset Audio Gateway
Service RecHandle: 0x10005
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 2
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: AVRCP Controller
Service Description: Audio Video Remote Control
Service Provider: Symbian Software Ltd.
Service RecHandle: 0x10006
Service Class ID List:
  "AV Remote" (0x110e)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: SyncMLClient
Service RecHandle: 0x10007
Service Class ID List:
  UUID 128: 00000002-0000-1000-8000-0002ee000002
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 10
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00000002-0000-1000-8000-0002ee000002)
    Version: 0x0100

Service Name: OBEX File Transfer
Service RecHandle: 0x10008
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 11
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Nokia OBEX PC Suite Services
Service RecHandle: 0x10009
Service Class ID List:
  UUID 128: 00005005-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 12
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005005-0000-1000-8000-0002ee000001)
    Version: 0x0100

Service Name: SyncML DM Client
Service RecHandle: 0x1000a
Service Class ID List:
  UUID 128: 00000004-0000-1000-8000-0002ee000002
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 13
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00000004-0000-1000-8000-0002ee000002)
    Version: 0x0100

Service Name: Nokia SyncML Server
Service RecHandle: 0x1000c
Service Class ID List:
  UUID 128: 00005601-0000-1000-8000-0002ee000001
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 14
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "" (0x00005601-0000-1000-8000-0002ee000001)
    Version: 0x0100

Service Name: OBEX Object Push
Service RecHandle: 0x1000d
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 9
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

Service RecHandle: 0x1000e
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3

Service Name: Dial-Up Networking
Service RecHandle: 0x1000f
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 4
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

Service Name: Imaging
Service RecHandle: 0x10010
Service Class ID List:
  "Imaging Responder" (0x111b)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 15
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x454e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Imaging" (0x111a)
    Version: 0x0100
```

So , I see dial up on channel 4. Then I edit /etc/bluetooth/rfcomm.conf
as 

```
rfcomm0 {
        # Automatically bind the device at startup
        bind yes;

        # Bluetooth address of the device
        device 00:1C:D4:47:D1:3C;

        # RFCOMM channel for the connection
        channel 4;

        # Description of the connection
        comment "Ondra 95";
}

```

An then I restart the bluetooth. It should be ok and in /dev/ i should see rfcomm0. No way, even if I do from command line rfcomm, nothin appears.

Whats wrong. Is this a problem with udev again? Please, this is urgent.

---

### Post by oyankee on 2009-10-31
I have found solution:

```
rfcomm conncect /dev/rfcomm0 00:1C:D4:47:D1:3C 4
```

Now, rfcomm0 is visible and I can connect to it via bluetooth and ppp aplication.

---

### Post by Wuphon on 2009-11-01
> **oyankee said:**
> I have found solution:

```
rfcomm conncect /dev/rfcomm0 00:1C:D4:47:D1:3C 4
```Now, rfcomm0 is visible and I can connect to it via bluetooth and ppp aplication.


It looks like the bluetooth script in /etc/init.d does not run the "rfcomm bind" command in karmic.  That would have made /dev/rfcomm0 visible.  

Maybe you could try  /etc/init.d/bluetooth from 9.04,  that does include initializing rfcomm.

---

### Post by oyankee on 2009-11-01
Yes that could solve the problem. But to be honest, I am glad to have it right as it is. I´ll just report a bug for now.

---

### Post by mantakbilug on 2009-11-04
> **oyankee said:**
> Yes that could solve the problem. But to be honest, I am glad to have it right as it is. I´ll just report a bug for now.

I encountered this problem too. In particular I found that the rfcomm module is missing from the kernel. 

giving the command

modinfo rfcomm

the result is:

ERROR: modinfo: could not find module rfcomm


Someone opened the bug report? Which is the ID?

---

### Post by mikeh on 2009-11-05
> **mantakbilug said:**
> 
ERROR: modinfo: could not find module rfcomm

I still see that, even when rfcomm is working.

---

### Post by mantakbilug on 2009-11-08
Sorry but I still can't connect with GNOME PPP.
If I run the command:
rfcomm conncect /dev/rfcomm0 00:1C:D4:47:D1:3C 4

I can connect only by network manager, configuring the broadband. In this way I can't control the connection time, there is not a counter anywhere, and for me this function is essential!
The only solution is to use GNOME PPP, but I have to solve the problem with rfcomm0.

There is a BUG, It 'obvious, no one has reported?

---

### Post by audunlea on 2009-11-09
I've got the same problem, so I hope someone report this bug 

Regards
Audun

---

### Post by mantakbilug on 2009-11-09
> **audunlea said:**
> I've got the same problem, so I hope someone report this bug 

Regards
Audun


Here the bug report:
[https://bugs.launchpad.net/ubuntu/+bug/479239](https://bugs.launchpad.net/ubuntu/+bug/479239)

---

