---
title: "how to get kaan kobil cardreader to work ?"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by AndreasMeier on 2005-07-06
Hi,

I'm trying to get my Kaan Kobil Standard Plus smartcard reader to work.
System is Kubuntu Hoary. Kernel is 2.6.10-5-k7.
I have downloaded the driver from [www.kobil.com](www.kobil.com) and copied the libct.so in /usr/lib

When I try modprobe kobil_sct, I receive no error message, so I think the module is loaded correctly.

In addition I gave rights to ttyUSB* with chmod 666 /dev/ttyUSB* to have access.

But all did not help, when I try to test the cardreader with Moneyplex, I only receive the message, that the reader is still not accessible.

What do I have to do in addition to get it run ? 

Thanks for your advice,
Regards
Andreas

---

### Post by AndreasMeier on 2005-07-09
When I use the cardping program from Kobil,
I receive with command "cardping -b2" following result:
CT_init (Port 2): 0
CT_Reset: -1

In the file CT_devices is the following:
GetPortType=#0
SetPortType=#0
DefaultPortType=#0
DefaultProtocollType=#0
UseOnlyDefaultProtocoll=#0
B1DTRLow=#50
B1DSRRespActive=#2000
PnPChar=#150
B1WaitForPnPString=#1500
KaanWaitForPnPString=#600
Port1=COM;/dev/ttyUSB0;2;0;serial reader at /dev/ttyUSB0: Kaan/SecOVID/TWIN

Is this the problem that cardping reports on -b2, which should be Port2 with my understanding and 
in the CT_devices there is Port1 ?

Can anyone help me here please ?

regards
Andreas

---

### Post by AndreasMeier on 2005-07-12
Anyone here able to help me, please ??!!

---

### Post by AndreasMeier on 2005-07-31
I read in another forum, that Moneyplex is looking for the cardreader on ttyUSB,
but in Ubuntu the cardreader is on ttyUSB0.

So I thought, a symbolic link would help. I generated ttyUSB, but after a reboot, the link was gone.

So my question is, how can I generate a symbolic link, which is not gone after a reboot ??

Thanks for your input,
regards
Andreas

---

### Post by AndreasMeier on 2005-08-20
Folks,

you're really someone, who can give answers at all !  :neutral: 
Man, no answer from anybody.
Is the hardware so rare under Ubuntu-Users ? Dont guess so. Anyways ...

Now I got this nasty thing to work finally !
The only thing I tried now, was, that I connected the card reader AFTER the system was started.
The rest of the config thing was already done.

So, for anyone out there, seeking for an answer, dont give up and try this out.

Regards
Andreas

---

