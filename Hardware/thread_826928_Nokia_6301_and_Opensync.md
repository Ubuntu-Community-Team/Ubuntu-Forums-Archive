---
title: "Nokia 6301 and Opensync"
date: 2008-06-12
forum: Hardware
---

### Post by RicoD on 2008-06-12
Hi,

On Hardy, I'm trying to sync my Nokia 6301 (Phone with UMA and Wifi with firmware 4.61)with Opensync and Multisync0.9 (only with USB as my Hardy distro is on a desktop PC
Prerequisites are OK  (ici = [http://libsyncml.opensync.org/wiki/obex-guide#Usage](http://libsyncml.opensync.org/wiki/obex-guide#Usage)) 
"Interface description" is not showing "SYNCML-SYNC"

sudo syncml-obex-client -u
Found 3 USB OBEX interfaces
Interface 0:
        Manufacturer: Nokia
        Product: Nokia 6301
        Interface description: (null)
Interface 1:
        Manufacturer: Nokia
        Product: Nokia 6301
        Interface description: (null)
Interface 2:
        Manufacturer: Nokia
        Product: Nokia 6301
        Interface description: (null)


OpenSync errors
$ sudo syncml-obex-client -u 0 --identifier "PC Suite" --sync text/x-vcard Contacts --sync text/x-vcalendar Calendar --wbxml
connection with device succeeded
Received an Alert for the DS Server at Contacts: Type: 201, Last 0, Next 117
Received an Alert for the DS Server at Calendar: Type: 201, Last 0, Next 0
Just received a new session with ID 1
Received the DevInf
Session 1 reported final. flushing
Received an transport error: Request not successfull: 64

Wammu log : 

Sat 2008/06/07 17:44:15: [Gammu            - 1.18.90 built 21:19:18 Feb 13 2008 using GCC 4.2]
Sat 2008/06/07 17:44:15: [Connection       - "dku5"]
Sat 2008/06/07 17:44:15: [Connection index - 0]
Sat 2008/06/07 17:44:15: [Model type       - ""]
Sat 2008/06/07 17:44:15: [Device           - "/dev/ttyACM0"]
....
Sat 2008/06/07 17:44:41: Getting firmware versions
Sat 2008/06/07 17:44:41: 1 "AT+CGMR"
Sat 2008/06/07 17:44:41: 2 "V 04.61"
Sat 2008/06/07 17:44:41: 3 "15-10-07"
Sat 2008/06/07 17:44:41: 4 "RM-322"
Sat 2008/06/07 17:44:41: 5 "(c) Nokia            "
Sat 2008/06/07 17:44:41: 6 "OK"
Sat 2008/06/07 17:44:41: Received firmware version: "V 04.61"
Sat 2008/06/07 17:44:41: Entering GSM_GetModel
Sat 2008/06/07 17:44:41: Getting model
Sat 2008/06/07 17:44:41: 1 "AT+CGMM"
Sat 2008/06/07 17:44:41: 2 "Nokia 6301"
Sat 2008/06/07 17:44:41: 3 "OK"
Sat 2008/06/07 17:44:41: [Model: Nokia 6301]
...
Sat 2008/06/07 17:44:45: Checking for OBEX support
Sat 2008/06/07 17:44:45: 1 "AT+CPROT=?"
Sat 2008/06/07 17:44:45: 2 "ERROR"

Can someone check on his Nokia 6301 to see if he gets the same results : 
sudo syncml-obex-client -u

Found 3 USB OBEX interfaces
Interface 0:
        Manufacturer: Nokia
        Product: Nokia 6301
**        Interface description: (null)**

---

### Post by RicoD on 2008-06-14
Any advice ? 
Anyone wiuth a successfull sync with a 6301 ?

:confused:

---

### Post by RicoD on 2008-06-24
:(

Anyone with a successfull sync with a 6301 ?

---

