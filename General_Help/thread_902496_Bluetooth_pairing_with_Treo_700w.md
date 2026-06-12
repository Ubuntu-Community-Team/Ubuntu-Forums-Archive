---
title: "Bluetooth pairing with Treo 700w"
date: 2008-08-27
forum: General Help
---

### Post by HDave on 2008-08-27
I have a Verizon wireless PDA from Palm -- a Treo 700w.  It has windows mobile 5 on it and is bluetooth enabled.

I understand there is no easy way to sync with the PIM data, but has anybody successfully transfer files with it???

I can get through the pairing process (I think), but there are two problems:

1) Once paired, the treo doesn't list any of the available services (serial, dial-up, etc.)
2) When I try to browse the device from Ubuntu I get the following error.
```
Couldn't display "obex://[00:07:E0:7C:A6:98]/".
```

Based on other forum threads, I have already tried installing obextool and gnome-vfs-obexftp to no effect.

Any and all ideas are welcome!

---

### Post by snarebear on 2008-09-12
I have the same issue with my htc tytn with windows mobile 6. I still haven't come across a solution of where to enable the services.

---

### Post by Cresho on 2008-09-12
just to add some info on this insulting company called verizon, They purpously disable obex in all phones I have known and charge a fee to get your stuff out of the phone.  My bro went from at&t to verizon and back again.  Verizon branded phones have obex disabled and it pissed my brother off.  We both have the razr.  My friend has a verizon palm phone and has the same problem.  It is not a ubuntu gnome linux problem.  If you guys can do this obex in windows, its fine in linux.  If you have no problems with pim sync in windows, then your okay and I have no idea on how to get your phones synced to linux since I have no expirience.  I'm just telling you about the verizon THEME!

that is why when you search for services with the bluetooth, you come out with a fat blank!!!!!!!!!

---

### Post by Cresho on 2008-09-12
do this.  in phone, make sure it is not connected via bluetooth in any device and make the phone discoverable.  then open up the terminal and enter

sdptool browse

notice I have obex enabled from motorola and is not changed by at&t like verizon does to most or all the phones I have come accross.

services available from  my list tells me I have....
Dialup Networking Gateway
Voice Gateway
Handsfree Voice Gateway
OBEX Object Push
OBEX File Transfer
Image Push
Audio Source
Audio Video Remote Control Target


the one you seek is OBEX "object exchange" which allowes transfer of files from and to pda, phone, pc, etc.

```
sdptool browse
Inquiring ...
Browsing I EDITED THIS PART TO HIDE MY BLUETOOTH ID NUMBER SO SUCK IT UP! ...
Service RecHandle: 0x0
Service Class ID List:
  "SDP Server" (0x1000)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "SDP" (0x0001)
Profile Descriptor List:
  "SDP Server" (0x1000)
    Version: 0x0100

Service Name: Dialup Networking Gateway
Service Description: Dialup Networking Gateway
Service Provider: /a/mobile/cl.gif
Service RecHandle: 0x10001
Service Class ID List:
  "Dialup Networking" (0x1103)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x6573
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x7a68
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "Dialup Networking" (0x1103)
    Version: 0x0100

Service Name: Voice Gateway
Service Description: Headset Audio Gateway
Service Provider: /a/mobile/cl.gif
Service RecHandle: 0x10003
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 3
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x6573
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x7a68
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: Handsfree Voice Gateway
Service Description: Handsfree Voice Gateway
Service Provider: /a/mobile/cl.gif
Service RecHandle: 0x10007
Service Class ID List:
  "Handfree Audio Gateway" (0x111f)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 7
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x6573
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x7a68
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "Handsfree" (0x111e)
    Version: 0x0105

Service Name: OBEX Object Push
Service Description: OBEX Object Push
Service Provider: /a/mobile/cl.gif
Service RecHandle: 0x10008
Service Class ID List:
  "OBEX Object Push" (0x1105)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 8
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x6573
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x7a68
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

Service Name: OBEX File Transfer
Service Description: OBEX File Transfer
Service Provider: /a/mobile/cl.gif
Service RecHandle: 0x10009
Service Class ID List:
  "OBEX File Transfer" (0x1106)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 9
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x6573
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x7a68
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "OBEX File Transfer" (0x1106)
    Version: 0x0100

Service Name: Image Push
Service Description: Image Push
Service Provider: /a/mobile/cl.gif
Service RecHandle: 0x1000a
Service Class ID List:
  "Imaging Responder" (0x111b)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 10
  "OBEX" (0x0008)
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x6573
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x7a68
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "Imaging" (0x111a)
    Version: 0x0100

Service Name: Audio Source
Service Description: Audio Source
Service Provider: /a/mobile/cl.gif
Service RecHandle: 0x1000d
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x6573
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x7a68
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service Name: Audio Video Remote Control Target
Service Description: Audio Video Remote Control Target
Service Provider: /a/mobile/cl.gif
Service RecHandle: 0x1000e
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
  code_ISO639: 0x6573
  encoding:    0x6a
  base_offset: 0xc800
  code_ISO639: 0x7a68
  encoding:    0x6a
  base_offset: 0xc803
  code_ISO639: 0x6672
  encoding:    0x6a
  base_offset: 0xc806
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

```

---

