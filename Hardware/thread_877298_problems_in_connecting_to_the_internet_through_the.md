---
title: "problems in connecting to the internet through the notebook built in UMTS modem"
date: 2008-08-01
forum: Hardware
---

### Post by mpolito1969 on 2008-08-01
I've just burnt a CD with Ubuntu 8.04.1. I inserted it in the reader and powercycled my notebook (ASUS F3Sr).

The OS booted regularly and I tried to start my internet connection, the notebook has got an integrated GlobeTrotter UMTS-HSDPA modem.

I'm new to Ubuntu and the first thing I did was launching the "network settings" application.

You find attached some screenshot of my configuration. Every time I checked the ppp connection in the main window the window got opaque, a small well appeared (a kind of Windows hourglass) but after a few seconds the main window went back to its original state, without any box checked.

I tried selecting all modems I found in the "modem" tab but none of them gave any result.

I started Firefox but, as aspected, I was not connected to the internet.

I don't know where to start from for troubleshooting this issue.

I'd like to connect to the internet through the integrated modem, what should I do?

Under Windows Vista everything works right, so I don't think there is any hardware problem.

Thanks in advance.

Bye,
Max

---

### Post by phidia on 2008-08-01
Hi & Welcome to Ubuntu/linux. You almost certainly have a soft or winmodem-so called because they rely on the windows OS to work. (hardware functions were turned over to software)
So you have some choices you can try to get that modem working in linux. Do you like challenge? There's ample documentation [right here]("https://help.ubuntu.com/community/DialupModemHowto") to do that-provided the specific modem can be made to work with linux. The other choice is to buy an external modem be sure to find one that is linux compatible and use that.

---

### Post by mpolito1969 on 2008-08-01
> **phidia said:**
> There's ample documentation [right here]("https://help.ubuntu.com/community/DialupModemHowto") to do that-provided the specific modem can be made to work with linux.

It seems to me that it talks about "normal" modems, not UMTS ones. Do you think it applies to UMTS modems as well?

---

### Post by phidia on 2008-08-01
OK that's my fault for not paying better attention-sorry.
There is a guide for those [here]("http://tuxmobil.org/linux_on_laptops_with_umts_cards.html") but I'm not really going to be much help besides offering that link. I'm really not sure what a UMTS modem is.

---

### Post by mpolito1969 on 2008-08-02
I'm adding the information I get from Windows Vista:

Nome   [00000007] GlobeTrotter Module HSDPA Network Card   
Tipo scheda   Ethernet 802.3   
Tipo prodotto   GlobeTrotter Module HSDPA Network Card   
Installato   Sì   
ID periferica PNP   OPTIONBUS\GTS_FF_NET\6&33055F51&0&   
Ultima reimpostazione   27/07/2008 22.20   
Indice   7   
Nome servizio   GTMNDISIRPXP   
Indirizzo IP   Non disponibile   
Subnet IP   Non disponibile   
Gateway IP predefinito   Non disponibile   
DHCP abilitato   Sì   
Server DHCP   Non disponibile   
Scadenza lease DHCP   Non disponibile   
Lease DHCP ottenuto   Non disponibile   
Indirizzo MAC   00:F1:D0:00:F1:D0   
Driver   c:\windows\system32\drivers\gtm51irp.sys (1.0.0.6, 119,63 KB (122.496 Byte), 14/04/2007 14.05)    

and the output generated on Linux by dmesg.

It would also be useful understanding if, under Linux, this modem is seen as a serial, USB, PCMCIA or whatever else modem.

Ciao,
Max

---

### Post by mpolito1969 on 2008-09-04
I've found a solution, it's here:

[http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,508/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,508/)

Ciao,
Max

---

