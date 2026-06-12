---
title: "Pinnacle AV/DV Studio Capture Card"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by PedroX on 2007-02-14
I have a Pinnacle AV/DV Studio Capture Card PCI 500 Movieboard. When I do an lspci I get the following:

05:01.0 Multimedia controller: Pinnacle Systems Inc. AV/DV Studio Capture Card
        Subsystem: Pinnacle Systems Inc. Unknown device 0022
        Flags: bus master, medium devsel, latency 64, IRQ 193
        Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

But applications like MythTV or tvtime do not recognize the card. They keep saying no such device /dev/video. There is no /dev/video, but why can I see my card with lspci?


Any help would be appreciated.

I'm running Ubuntu Edgy (6.10).
Intel Core2Duo 6400
NVidia 7600GS

---

### Post by dwf_starband on 2007-06-18
I have the same problem,

Any ideas out there?

Thanks,

Dennis

---

### Post by dwf_starband on 2007-06-19
anyone?

---

### Post by skirkpatrick on 2007-06-19
Check your other thread: [http://ubuntuforums.org/showthread.php?t=477461](http://ubuntuforums.org/showthread.php?t=477461)

---

### Post by Deoden on 2007-08-31
> **PedroX said:**
> I have a Pinnacle AV/DV Studio Capture Card PCI 500 Movieboard. When I do an lspci I get the following:

05:01.0 Multimedia controller: Pinnacle Systems Inc. AV/DV Studio Capture Card
        Subsystem: Pinnacle Systems Inc. Unknown device 0022
        Flags: bus master, medium devsel, latency 64, IRQ 193
        Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

But applications like MythTV or tvtime do not recognize the card. They keep saying no such device /dev/video. There is no /dev/video, but why can I see my card with lspci?


Any help would be appreciated.

I'm running Ubuntu Edgy (6.10).
Intel Core2Duo 6400
NVidia 7600GS


Hi Pedrox

I have the same problem, but i have Pinnacle AV/DV Studio Capture Card PCI 700 Movieboard Plus. 

You resolve the problem????? Can you tell me anythink about it??

Thanks in advance.

PD: Sorry for my bad English.
__________________

---

### Post by dwf_starband on 2007-09-17
No, I never found anything out.  I ended up buying an actual tv tuner card w/ remote.  It should be here this week.

sorry for the bad news.

dennis

---

### Post by dosti00710 on 2007-12-20
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595). [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Please Send This Card Information on my email address

E-mail : [email]niraj.pandey.indore@gmail.com[/email]

---

### Post by dragman on 2007-12-29
HI i'm new of this forum excuse me for my english becouse I'm Italian .
I know that this card need zoran video driver in linux (I have it and I have the same your problem)
but the configuration of the kernel in ubuntu make you can't use this driver.what we must do?
Recompile al the kernel step by step? I hope no!
Tell me if you discover something else.

---

### Post by julipanno on 2008-01-16
After a lot of searching and getting some answers from Pinnacle I found out that this card uses the Conexant MB87J3560 chipset, the same as Studio 700, which is detailed here: [http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_Studio_700](http://www.linuxtv.org/v4lwiki/index.php/Pinnacle_Studio_700)
From the linuxtv wiki:
> This author has attempted to load all Conexant (cx*), BTTV (card=52), SAA*, IVTV and em28xx modules provided with the Linux 2.6.18 kernel but no /dev/video* devices appear after restarting udev. The test machine is an HP xw9300 Workstation running Debian Etch amd64.

In order for this card to work on Linux, a Pinnacle AV/DV2 Linux driver is needed to be written. (Or some way to use the Windows driver needs to be devised.) 

---

