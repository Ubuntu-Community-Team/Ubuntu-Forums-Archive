---
title: "I'm Leaving also (sorta!)"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by MedusaErodeus on 2005-04-13
I've been trying... For the past week to get My Linksys WPC11 (It's a B card for God Sake!!!).

Nothing works.... (Latest drivers, ndiswrapper, arthur's web page)...

It was working fine under Warty... (Why did I upgrade!!).

Now my laptop is useless...

I have my Ubuntu (Hoary) Desktop to get my fix... But my laptop... I miss my laptop...

I regrett to say that there's something broken with Hoary and Wireless...

---

### Post by XDevHald on 2005-04-13
Hey Medusa,

Sorry to hear about your technical issues with Hoary :(

Here are some quick links that will give you some info on your problems

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

or

[http://episteme.arstechnica.com/eve/ubb.x/a/tpc/f/96509133/m/312000212731](http://episteme.arstechnica.com/eve/ubb.x/a/tpc/f/96509133/m/312000212731)

I'm sorry if this is not helpful enough as I don't deal nor know much about the wireless area :( But I hope this will be useful to your hands :)

---

### Post by MedusaErodeus on 2005-04-14
Thanks....

Right now, I'm seriously considering getting a new PCMCIA NIC card.

Any suggestions as to what to get so it works out of the box?

I've seen the chart, but I'm more interested in actual user experience as to how easy it's to set it up.

Mind you, we're talking about HOARY!

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=MedusaErodeus]I've been trying... For the past week to get My Linksys WPC11 (It's a B card for God Sake!!!).

Nothing works.... (Latest drivers, ndiswrapper, arthur's web page)...

It was working fine under Warty... (Why did I upgrade!!).

Now my laptop is useless...

I have my Ubuntu (Hoary) Desktop to get my fix... But my laptop... I miss my laptop...

I regrett to say that there's something broken with Hoary and Wireless...[/QUOTE]

I have that exact card and it works fine. You should try to compile your own modules, that worked for me. 

Do what this howto says. I got my same card to work. Also try installing a different kernel and running that (say 686).

[http://www.ubuntulinux.org/wiki/OrinocoMonitorKimset2005Hoary/view?searchterm=kismet](http://www.ubuntulinux.org/wiki/OrinocoMonitorKimset2005Hoary/view?searchterm=kismet)

---

### Post by greenwom on 2005-04-26
I've tried the wiki and have problems with the third step

when I dpkg the kismet file I get an error.

the file in the wiki looks to be wrong

you wget the kismet file 2005.05
and he wants you to dpkg a 2005.01 (this seem simple but neither work)

to dpkg and install I need to enter dpkg -i  ****.deb ??? right

EDIT:   

root@mikesubuntu:~ # dpkg -i k*
(Reading database ... 60378 files and directories currently installed.)
Preparing to replace kismet 2005.04.R1-1 (using kismet_2005.04.R1-1_i386.deb) ...
Unpacking replacement kismet ...
dpkg: dependency problems prevent configuration of kismet:
 kismet depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 kismet depends on libgmp3; however:
  Package libgmp3 is not installed.
dpkg: error processing kismet (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kismet


WHat do I do with this ??

---

### Post by greenwom on 2005-04-26
I hate to reply to myself but for the sake of other trying t:o do this.

When I dpkg the kimset_2005.05.r1.1 file I recieved dependancy errors.

I used apt-get -i install libglib1.2 libgmp3
and that fixed the problem

then dpkg -i worked.


My question after going through all these steps is do I have to shut down the card  every time with 
#sudo ifdown eth1

edit-- I see building modules, stage 2 (how much longer  9:35 PM Chicago Time)

---

### Post by greenwom on 2005-04-26
Another problem (for the new bees ) that I've encountered.

Almost at the bottom of the wiki......

edit /etc/kismet/kismet.config for your card
use orinoco,eth1,orinocosource as the capture source

I entered the information  in the portion that said (incaps)

YOU MUST CHANGE........
source=, 

hope it's right

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=greenwom]Another problem (for the new bees ) that I've encountered.

Almost at the bottom of the wiki......

edit /etc/kismet/kismet.config for your card
use orinoco,eth1,orinocosource as the capture source

I entered the information  in the portion that said (incaps)

YOU MUST CHANGE........
source=, 

hope it's right[/QUOTE]

the line should be 

source=orinoco,eth1,orinocosource

---

### Post by greenwom on 2005-04-27
Well the line does match, I'll doule check it again...

But I'm still down and IWCONFIG still shows 'no wireless extensions'

so is there a place to look at the PCMIA, I just looked a a post describing it a bit but I'm not sure what to do....

---

### Post by nikolokolus on 2005-04-27
[QUOTE=MedusaErodeus]Thanks....

Right now, I'm seriously considering getting a new PCMCIA NIC card.

Any suggestions as to what to get so it works out of the box?

I've seen the chart, but I'm more interested in actual user experience as to how easy it's to set it up.

Mind you, we're talking about HOARY![/QUOTE]

i can tell you that the atheros based D-link DWL-G650 (802.11b/g/superg*) works rather well and requires no extra futzing (unless you need WPA support).  I saw some on e-bay for around 24.00 (U.S. dollars)

*note:  Super g mode under linux does nothing, but it doesn't hurt it either

---

### Post by darkxb on 2005-05-14
i bought a hawking card, the hwc54g that supposedly was a prism gt chipset card, but i may take it back and order a 650 from dlink, since i cant get this card to even activate or light up for the life of me. thanks nikolokolus

---

