---
title: "Extracting audio data from voice modem [programming]"
date: 2008-12-06
forum: Hardware
---

### Post by josephdaniel on 2008-12-06
Hi,

I have been trying to develop a simple program to perform the same functionality of this windows application under linux.
[http://www.twilightutilities.com/PhoneServer.html](http://www.twilightutilities.com/PhoneServer.html)

The program allows a client connected over the internet to make phone calls using a voice modem installed at the server computer. It's like having a personal PC2Phone solution. You can use your home phone line you already pay for to make calls anywhere you have an internet connection.

On ubuntu, I have been experimenting with AT commands for voice modem capabilities; the commands AT+VRX and AT+VTX enable me to read and write voice data to the phone line. However, I have failed to use them simultaneously. I can only receive voice data or transmit it one way at a time. The modem won't allow it. I have tried with two different modems with the same result.

I read about mgetty-voice but it doesn't allow direct control of voice data. It can only be used for voicemail.

My question is: How can I read and write voice data to the modem simultaneously? Is there something similar to TAPI for windows?

Excuse me if this question is the wrong section. It's my first linux development related post and I'd appreciate it if you guide me to the correct section.

Thanks,
Joseph

---

### Post by Elludium_Q-36 on 2009-04-24
in Adept or Synaptic package manager, do searches for:

*  asterisk
*  bayonne
*  iax
*  pstngw
*  yate

Asterisk is the most developed telephony server of the group, most supported and has client applications (kiax) as well as a portable client (iaxcomm).


Pstngw is an H.323 to PSTN gateway,

Bayonne and yate are also for telephony.

The description from the asterisk package:

Asterisk is an Open Source PBX and telephony toolkit. 
It is, in a sense, middleware between Internet and telephony channels on the bottom, and Internet and telephony applications at the top.
Asterisk can be used with Voice over IP (SIP, H.323, IAX and more) standards, or the Public Switched Telephone Network (PSTN) through supported hardware.

Supported hardware:
* All Wildcard (tm) ISDN PRI cards from Digium ([http://www.digium.com](http://www.digium.com)) 
* HFC-S/HFC-4S-based ISDN BRI cards (Junghanns.NET, beroNet, Digium etc.) * All TDM (FXO/FXS) cards from Digium 
* Various clones of Digium cards such as those by OpenVox 
* Xorcom Astribank USB telephony adapter ([http://www.xorcom.com](http://www.xorcom.com)) 
* Voicetronix OpenPCI, OpenLine and OpenSwitch cards 
* CAPI-compatible ISDN cards (using the add-on package chan-capi) 
* Full Duplex Sound Card (ALSA or OSS) supported by Linux 
* Tormenta T1/E1 card ([http://www.zapatatelephony.org](http://www.zapatatelephony.org)) 
* QuickNet Internet PhoneJack and LineJack ([http://www.quicknet.net](http://www.quicknet.net))

I have also read of linksys routers being converted to lightweight asterisk servers, for a single telephone line...

[http://www.voip-info.org/wiki/view/Asterisk+Linksys+WRT54G](http://www.voip-info.org/wiki/view/Asterisk+Linksys+WRT54G)


There is an API package for asterisk, python-asterisk.

Asterisk management/administration and operator packages include:
*destar
*gastman
*op-panel

You may find in your search, openam that is an answering machine but only for H.323

Also isdnvbox is an ISDN answering machine.

Search adept or synaptic for mgetty and vgetty for related packages but mgetty-voice is the pertinent one to your query.

No sense reinventing the wheel if Asterisk or maybe Bayonne would do what you need.  There is much online documentation for Asterisk, in many languages...

Good luck.

---

