---
title: "Internet card problems"
date: 2008-04-23
forum: Hardware
---

### Post by racrbilly67 on 2008-04-23
I have a HP dv6604nr laptop. I have downloaded and installed Ubuntu 7.1 64bit edition. I am having trouble connecting to the internet. Because my wireless card does not work out of the box. So I cannot connect to the internet at all. Does anyone know what to do to fix this?

---

### Post by Patsoe on 2008-04-23
[https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr)](https://wiki.ubuntu.com/HP_Pavillion_dv6000_(dv6604nr))

Hope that helps, if not, do post back!

---

### Post by racrbilly67 on 2008-04-26
OK I have tried that thread but I keep getting an error. I have done it before but I was connected to the internet with a different internet card. But I have tried using that card and it does not connect to my network or it does and then it does not let me on the internet and then it will kick me off like every 5 minutes. Or if someone can tell me if the new Ubuntu supports my card then I will just upgrade to the new version.

---

### Post by Patsoe on 2008-04-26
> **racrbilly67 said:**
> OK I have tried that thread but I keep getting an error. 
That isn't a lot of information :)

> Or if someone can tell me if the new Ubuntu supports my card then I will just upgrade to the new version.
So are you talking about the built-in Broadcom stuff or your other card (what brand and model?)? Broadcom wlan support will always be crappy until they start supporting Linux. But it wouldn't do harm to try 8.04 I guess.

---

### Post by racrbilly67 on 2008-04-27
OK yea I know that is not a lot of information. Sorry about that. I am not doing anything today so I will be able to log into ubuntu and actually give you my errors from the terminal.

My other card is a netgear WG111v2 and from my understanding is supposed to be supported by 7.1. So I don't know what to do. When I tried plugging in to my router via ethernet cable my computer did not get an IP address but was able to recognize the connection.

I will get back later today with more information. I am very familiar with the Windows operating system but not very with Linux. So you will have to bear with me because I do not know a lot.

---

### Post by Patsoe on 2008-04-27
Well you could try if things run out of the box with the Netgear dongle, but from what I gather, that's not a very OSS-friendly product either.

Maybe your best chances are wrapping the Windows XP drivers from HP with ndiswrapper. That's what I did in the end.

[http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html](http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html) has a description for a Dell machine. Of course the part about extracting the WinXP driver is different - I used cabextract on the HP driver package.

---

