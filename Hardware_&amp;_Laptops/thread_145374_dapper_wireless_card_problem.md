---
title: "dapper wireless card problem"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by hapee on 2006-03-16
I installed dapper on my laptop (a topline amicus) and have problems installing my wifi card (which was working on breezy without problem). 

I tried with ndiswrapper and with several bootoptions but dmesg keeps on saying :

cs: pcmcia_socket0: cardbus are not supported

is this Dapper or the kernel?

lspci says:

0000:00:0a.0 Cardbus bridge: 02 Micro, Ind 0Z6812 Cardbus Controller (rev 05)

nsdiswrapper -l  says:

installed ndis drivers:
rt2500 driver present

So I am stuck, any suggestion?

Thanks,

Hapee

---

### Post by hapee on 2006-03-16
any comment on this? or am I in the wrong forum and should I move to network?

---

