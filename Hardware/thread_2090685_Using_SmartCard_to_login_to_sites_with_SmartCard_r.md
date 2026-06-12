---
title: "Using SmartCard to login to sites with SmartCard reader"
date: 2012-12-03
forum: Hardware
---

### Post by alex-s77 on 2012-12-03
Hello

I would "*like*" to use a certificate (&#8594; [SuisseID]("http://postsuisseid.ch/de/suisseid")) stored on a SmartCard to login to certain sites (&#8594; eg. shopping site [brack.ch]("http://www.brack.ch/tabid/44798/Default.aspx")). The SmartCard is "installed" in a [Cherry ST-2000U]("http://www.cherry.de/cid/katenlesegeraete_SmartTerminal_ST-2000U.htm") SmartCard Reader.

*My question basically is: **How do I get a browser** (Firefox, Chrome, Opera &#8212; I don't care&#8230;) **to read the certificate from the SmartCard in the SmartCard reader?***

After some fiddling around (don't remember the details&#8230;), "the system" recognizes the SmartCard in the SmartCard reader. Ie. **pcsc_scan**, **opensc-tool** and also **pkcs15-tool** are able to read from the SmartCard. See the attached files for more output. This shows (?) to me, that the basic functionality seems to be okay. 

But how to "integrate" it in the browser?

I'm lost&#8230; :(

Can someone please help?

Thanks,
Alexander

```
########################################### pcsc_scan
########################################### see below for output from:
########################################### opensc-tool
########################################### or:
########################################### pkcs15-tool

$ pcsc_scan
PC/SC device scanner
V 1.4.20 (c) 2001-2011, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.8.3
Using reader plug'n play mechanism
Scanning present readers...
0: Cherry GmbH SmartTerminal ST-2xxx [Vendor Interface] (21121217150782) 00 00

Fri Nov 30 12:21:02 2012
Reader 0: Cherry GmbH SmartTerminal ST-2xxx [Vendor Interface] (21121217150782) 00 00
  Card state: Card inserted, 
  ATR: 3B FA 18 00 02 C1 0A 31 FE 58 4B 53 77 69 73 73 53 69 67 6E 89

ATR: 3B FA 18 00 02 C1 0A 31 FE 58 4B 53 77 69 73 73 53 69 67 6E 89
+ TS = 3B --> Direct Convention
+ T0 = FA, Y(1): 1111, K: 10 (historical bytes)
  TA(1) = 18 --> Fi=372, Di=12, 31 cycles/ETU
    129032 bits/s at 4 MHz, fMax for Fi = 5 MHz => 161290 bits/s
  TB(1) = 00 --> VPP is not electrically connected
  TC(1) = 02 --> Extra guard time: 2
  TD(1) = C1 --> Y(i+1) = 1100, Protocol T = 1 
-----
  TC(2) = 0A --> Work waiting time: 960 x 10 x (Fi/F)
  TD(2) = 31 --> Y(i+1) = 0011, Protocol T = 1 
-----
  TA(3) = FE --> IFSC: 254
  TB(3) = 58 --> Block Waiting Integer: 5 - Character Waiting Integer: 8
+ Historical bytes: 4B 53 77 69 73 73 53 69 67 6E
  Category indicator byte: 4B (proprietary format)
+ TCK = 89 (correct checksum)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B FA 18 00 02 C1 0A 31 FE 58 4B 53 77 69 73 73 53 69 67 6E 89
	SuisseId card (used for qualified signatures)
	http://postsuisseid.ch/de/suisseid
	http://www.suisseid.ch/
^C


########################################### opensc-tool

alexander@ewzw032:~$ opensc-tool --list-readers
# Detected readers (pcsc)
Nr.  Card  Features  Name
0    Yes   PIN pad   Cherry GmbH SmartTerminal ST-2xxx [Vendor Interface] (21121217150782) 00 00

alexander@ewzw032:~$ opensc-tool --reader 0 --name
Card not present.

alexander@ewzw032:~$ opensc-tool --reader 0 --name -v
Connecting to card in reader Cherry GmbH SmartTerminal ST-2xxx [Vendor Interface] (21121217150782) 00 00...
Using card driver Default driver for unknown cards.
Card name: Unsupported card



########################################### pkcs15-tool

alexander@ewzw032:~$ pkcs15-tool  -D
Using reader with a card: Cherry GmbH SmartTerminal ST-2xxx [Vendor Interface] (21121217150782) 00 00
PKCS#15 Card [SwissSignID                     ]:
        Version        : 0
        Serial number  :
        Manufacturer ID: SwissSign
        Flags          : Login required, PRN generation

PIN [PIN]
        Object Flags   : [0x3], private, modifiable
        Auth ID        : 02
        ID             : 01
        Flags          : [0x11], case-sensitive, initialized
        Length         : min_len:5, max_len:12, stored_len:0
        Pad char       : 0x00
        Reference      : 129
        Type           : UTF-8

PIN [SO-PIN]
        Object Flags   : [0x3], private, modifiable
        ID             : 02
        Flags          : [0x99], case-sensitive, unblock-disabled, initialized, soPin
        Length         : min_len:6, max_len:12, stored_len:0
        Pad char       : 0x00
        Reference      : 130
        Type           : UTF-8

PIN [Secondary Authentication PIN]
        Object Flags   : [0x3], private, modifiable
        Auth ID        : 02
        ID             : 03
        Flags          : [0x13], case-sensitive, local, initialized
        Length         : min_len:6, max_len:12, stored_len:0
        Pad char       : 0x00
        Reference      : 144
        Type           : UTF-8
        Path           : 3f005015

PIN [Digital Signature PIN]
        Object Flags   : [0x3], private, modifiable
        Auth ID        : 12
        ID             : 11
        Flags          : [0x13], case-sensitive, local, initialized
        Length         : min_len:6, max_len:12, stored_len:0
        Pad char       : 0x00
        Reference      : 129
        Type           : UTF-8
        Path           : 3f001fff

Private RSA Key [SwissSign_nonRep                ]
        Object Flags   : [0x3], private, modifiable
        Usage          : [0x204], sign, nonRepudiation
        Access Flags   : [0x1D], sensitive, alwaysSensitive, neverExtract, local
        ModLength      : 2048
        Key ref        : 2 (0x2)
        Native         : yes
        Path           : 3f001fffc100
        Auth ID        : 11
        ID             : 935abf517aa9398583b10474f64c8e826543a876

Private RSA Key [SwissSign_digSig                ]
        Object Flags   : [0x3], private, modifiable
        Usage          : [0x26], decrypt, sign, unwrap
        Access Flags   : [0x1D], sensitive, alwaysSensitive, neverExtract, local
        ModLength      : 2048
        Key ref        : 2 (0x2)
        Native         : yes
        Path           : 3f00501550724b025502
        Auth ID        : 01
        ID             : ×××

Private RSA Key [SwissSign_dataEnc               ]
        Object Flags   : [0x3], private, modifiable
        Usage          : [0x26], decrypt, sign, unwrap
        Access Flags   : [0x1D], sensitive, alwaysSensitive, neverExtract, local
        ModLength      : 2048
        Key ref        : 3 (0x3)
        Native         : yes
        Path           : 3f00501550724b035503
        Auth ID        : 01
        ID             : ×××

Public RSA Key [SwissSign_nonRep                ]
        Object Flags   : [0x2], modifiable
        Usage          : [0x40], verify
        Access Flags   : [0x0]
        ModLength      : 2048
        Key ref        : -1
        Native         : no
        Path           : 3f001fffc100
        ID             : ×××

Public RSA Key [SwissSign_digSig                ]
        Object Flags   : [0x2], modifiable
        Usage          : [0x51], encrypt, wrap, verify
        Access Flags   : [0x10], local
        ModLength      : 2048
        Key ref        : -1
        Native         : no
        Path           : 3f00501550754b02
        ID             : ×××

Public RSA Key [SwissSign_dataEnc               ]
        Object Flags   : [0x2], modifiable
        Usage          : [0x51], encrypt, wrap, verify
        Access Flags   : [0x10], local
        ModLength      : 2048
        Key ref        : -1
        Native         : no
        Path           : 3f00501550754b03
        ID             : ×××

```

---

