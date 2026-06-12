---
title: "evolution nokia E63 PIM sync"
date: 2011-01-24
forum: Hardware
---

### Post by treehermit on 2011-01-24
Hi,

I've searched linux forums & google for 3 weeks before posting this question. 

I need to sync my Nokia E63 with Evolution using USB/ bluetooth. Please find the following details:
[B]
Desktop (Hardware):[/B]
Dell Inspiron (E1705) 9400 series.
Intel Core Duo

**Desktop (OS):**
Ubuntu 10.10 Meerkat
Evolution ver. 2.30.3


[B]Mobile:
Nokia E63[/B]

[LIST]
[*]S60 3.1 Edition
[*]Symbian Os 9.2
[/LIST]


The following is the capabilities for data transmission in my phone:
**Data network**  
[LIST]
[*]CSD
[*]HSCSD
[*]GPRS class A, multislot class 32, maximum speed 100/60 kbps (DL/UL)
[*]EDGE class A, multislot class 32, maximum speed 296/177.6 kbps (DL/UL)
[*]WCDMA 900/2100 or 850/1900 or 850/2100, maximum speed 384/384 kbps (DL/UL)
[*]WLAN IEEE 802.11b/g
 - WLAN Security: WEP, 802.1X, WPA, WPA2
[*]TCP/IP support
[*]IETF SIP and 3GPP
[/LIST]
  
**Local connectivity and synchronization**
  
[LIST]
[*]Bluetooth version 2.0 with Enhanced Data Rate
 - Bluetooth profiles: DUN, OPP, FTP, HFP, GOEP, HSP, BIP, RSAP, GAVDP, AVRCP, A2DP
[*]MTP (Multimedia Transfer Protocol) support
[*]Bluetooth (Bluetooth Serial Port Profile. BT SPP)
[*]Network (Raw). Direct TCP/IP socket
 connection to any specified port (a.k.a HP
 JetDirect™).
[*]Network (LPR). Line Printer Daemon
 protocol (RFC1179).
[*]Support for local and remote SyncML synchronization, iSync, Intellisync, ActiveSync
[/LIST]
So far I have tried the following options:

_multisync:_ requires some open-obex-client which is no longer supported in the ubuntu repositories

_syncML & funambol:_ am having problems syncing evolution to funambol & thunderbird wont sync notes with funambol

_xgnokii_: doesnt load on my ubuntu desktop

_wammuu: _not compatible with my phone

also tried to load nokia PC suite with Wine... the software runs but cannot connect to my phone

Although I can currently send files from my PC to the E63 via the native ubuntu bluetooth packages, i cant browse the phones folders.

Please help me!

I might have to go back to windows if I cant sync my office related calendar & notes in Linux.. I cant bear the thought of having to put up with windows after experiencing ubuntu :( 


I cant afford the $10.00/month fee by Ubuntu One for mobile sync of calendar & notes, but I am willing to change my phone if i'm assured that it'll talk to evolution on my PC

also, would my current phone sync with ubuntu 9/ 10.04, or xubuntu, or kubuntu?

ANY solution will be muchly appriciated

---

### Post by treehermit on 2011-04-05
wow,

348 views & not one single reply!!

BUMP

:guitar:

---

### Post by Ramon444 on 2011-04-25
Try this: [http://tech.onagenda.com/en/linux/ubuntu/sincronizacion-nokia-e71-evolution-y-ii/#eedd00]("http://tech.onagenda.com/en/linux/ubuntu/sincronizacion-nokia-e71-evolution-y-ii/#eedd00")
For me it helped. I have Nokia E51.

BUT: I added stable repository instead of unstable(syncevolution from manual didn't worked for me): deb [http://downloads.syncevolution.org/apt](http://downloads.syncevolution.org/apt) stable main

---

### Post by treehermit on 2011-06-01
Hi Ramon444,

it didnt work. I tried installing all available versions of syncevolution in both the stable & unstable repositories..

my phone is able to connect but the sync keeps failing.. 

i'm attaching the error msg in the gui of 'sync'.. where do you think i can go from here?

---

### Post by Ramon444 on 2011-06-01
GUI error message don't give enough information. Try to run in console and look what it will say. Before i have found this manual i have used google for syncing my contacts. And sync-evo always gave me an error (like problems with address book) after deleting it, i had successful sync.

---

### Post by Irihapeti on 2011-06-01
I have a Nokia E63 which I sync using syncevolution (from the downloads.syncevolution.org repository) in Ubuntu 10.04. So, yes, it should work.

I've had problems with sync-ui not finding the calendar. I found I had best results setting up with sync-ui and then running the actual sync by command line. You could try deleting all the syncevolution configuration files in .config and starting again.

It might also be worth posting your query on the syncevolution mailing list: [http://lists.syncevolution.org/listinfo/syncevolution](http://lists.syncevolution.org/listinfo/syncevolution) or, if you prefer a GUI, [http://dir.gmane.org/gmane.comp.mobile.syncevolution](http://dir.gmane.org/gmane.comp.mobile.syncevolution) The developer has helped me out on more than one occasion.

---

