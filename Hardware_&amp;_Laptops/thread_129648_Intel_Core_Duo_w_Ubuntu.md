---
title: "Intel Core Duo w/ Ubuntu"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by vrode on 2006-02-14
Looking for any feedback.

Is anyone is running ubuntu 5.10 on intel core duo processor?

I'm looking at getting ThinkPad T60 w/ the following config:

Intel® Core Duo processor T2400 1.83GHz
14.1"
1400x1050
64MB ATI Mobility Radeon X1300


regards,
/virendra

---

### Post by alfonz on 2006-02-14
I think is should be ok, just make sure you install the i686 smp kernel, it will use the dual core features of your cpu.

---

### Post by vrode on 2006-02-14
Any hicups w/ applications?



regards,
/virendra

---

### Post by alfonz on 2006-02-14
im not sure, I'm using the smp kernel on my p4 with HyperThreading (it recognized this too) and I don't have any problems so far, at least none that I have noticed.

---

### Post by Scotland on 2006-02-14
[QUOTE=vrode]Looking for any feedback.

Is anyone is running ubuntu 5.10 on intel core duo processor?

I'm looking at getting ThinkPad T60 w/ the following config:

Intel® Core Duo processor T2400 1.83GHz
14.1"
1400x1050
64MB ATI Mobility Radeon X1300


regards,
/virendra[/QUOTE]


I run Ubuntu with kubuntu-desktop on my Dell Inspiron 9400. Had to compile a custom kernel as the Dell has no PCMCIA and this caused the default 686 smp kernel to hang trying to start PCMCIA, 

One other issue is that there is no Intel Wireless 3945 Driver available for Linux as yet (intel site says Driver Expected Q1 2006), wired works automatically.

Regards,

Dougie.

---

### Post by vrode on 2006-02-14
The thinkpad that I'm looking comes w/ Intel PRO/Wireless 3945ABG. I'm guessing this should be ok.

I'll search the archives for any issues on the wi-fi card, if not, I'll post it to wi-fi forum.


Appreciate all who responded!


regards,
/virendra

---

### Post by Kenotic on 2006-02-14
Some of us are trying to get the 3D working on our Acers with core duo. The proc is fine and runs great, but the damn x1400s are killing me.

---

### Post by mips on 2006-02-14
Google for the 3945 as I dont think it is supported yet. Intel says Q1 2006 availability.

[http://support.intel.com/support/notebook/sb/cs-006408.htm](http://support.intel.com/support/notebook/sb/cs-006408.htm)

---

### Post by vrode on 2006-02-14
Is it fair to say that I should stay away from core duo processor for now?



regards,
/virendra

---

### Post by mips on 2006-02-15
I would not say that. Just be prepared not to have access to the wireless for now. You could always get a Cisco PCMCIA (or other) card of ebay for cheap in the mean time which would also make a nice spare. Be carefull if you get a mPCI card as they might have bios lockouts.

Alternatively you could order it with a 2200BG card ?

---

### Post by vrode on 2006-02-16
Actually I've decided to stick w/ a single pentium m processor for now (ibm t43).

thanks for everyone who responded!



regards,
/virendra

---

### Post by mips on 2006-03-02
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

---

### Post by kingsidy on 2006-03-02
mips did you actually get it to work. I mean wireless card

---

### Post by mips on 2006-03-03
[QUOTE=kingsidy]mips did you actually get it to work. I mean wireless card[/QUOTE]

I do not have a 3945ABG but an 2200BG so cannot try.

If anybody would want to give me a 3945ABG I would give it a bash ;)

---

### Post by snyderg on 2006-03-05
I am using the new Dell E1705 w/Duo Core.

kernel 2.6.12.10  686.smp  (Kinfo shows two processors) I had to disable pcmcia at start up because it freezes with this kernel, haven't checked it out yet

Nvidia 256m 7800 works

Everything else works (don't know about modem yet) except the wireless - Intel Pro 3945

---

### Post by digitalextortion on 2006-04-10
I as well have a Dell e1705 with the core duo. I am currently running the Dapper Drake install.

-Dual core works great with the i686 smp kernel ( no pcmcia hang like others have been reporting )

-Sound was fixed in the latest kernel update ( had broken intel HDA sound apparently ) all buttons work, volume, play stop etc.

-7800go 256 runs great ! with full hardware 3D support for games through transgaming. Playing eve at full screen 1920x1200 with sound :D

-Only thing not working is the internal wireless Dell Truemobile 1390 support. I have been unable to get this working with ndiswrapper so far. Anyone else have any luck?

---

### Post by mips on 2006-04-10
The Intel3945 seems to work ok in Dapper, [http://www.ubuntuforums.org/showthread.php?t=140085](http://www.ubuntuforums.org/showthread.php?t=140085)

---

### Post by demessmaker on 2006-04-11
Hi all,

Managed to solve the pcmcia on  kernel 2.6.12.10 686.smp hang issue on a Dell 9400 by installing BUM (Boot-Up Manager) and turning off pcmcia support in the services tab.

Still working on the wireless issue.

Will keep you posted.

---

### Post by f0n1x m0nk3y on 2006-04-18
I have the Dell 1390 wireless mini card and cannot find drivers for that.  Any idea how I can get that to work?

Ubuntu found both cores on my laptop.

---

### Post by mips on 2006-04-18
[QUOTE=f0n1x m0nk3y]I have the Dell 1390 wireless mini card and cannot find drivers for that.  Any idea how I can get that to work?

Ubuntu found both cores on my laptop.[/QUOTE]

I 'think' that card uses a Broadcom chipset but I could be mistaken. You need to identify the chipset first.

[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)
[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

---

### Post by spiritofreason on 2006-04-20
The chipset for the Dell TrueMobile 1390 is BCM4311.  There was a report of it [working with ndiswrapper ]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D") for someone with the e1505.  The driver is the same for e1705 and e1505, so perhaps it will work.  However, I have heard that the version of ndiswrapper in the repositories isn't new enough to have support for it.

Hopefully that helps.

---

### Post by terrell on 2006-04-22
I have a e1505 with the TrueMobile 1390 wireless card working with Dapper. It will work with Breezy as well though... just download the newest ndiswrapper from sourceforge, and with the driver from Dell you should be good.

---

### Post by MarkBaum on 2006-05-01
Do you have to use ndiswrapper on Dapper also for the dell 1390?  I'm getting a 9400 in a couple days and I plan on installing at least Ubuntu, and maybe Gentoo(I'm a sucker for multiple OS's)  I have the dell wifi card.

---

### Post by GLTHFJ60 on 2006-10-31
What is the command, or where do I get the command for downloading the i686 smp kernel?  I have a duo core and I want to make sure that I have it installed.

Thanks.

---

