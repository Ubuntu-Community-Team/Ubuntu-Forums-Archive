---
title: "Wifi assistance"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by carolinamagi on 2007-10-14
Hello all! I'm sorry to bother you with this . . .
I'm brand spanking new to linux and i chose Ubuntu after spending the past five months scouring the internet for reasons *not* to install ubuntu. I hate the boys in Redmond and thought I'd give ubuntu a go.

Anyhow . . . so far I love what I see but there is one small issue: the wifi

I have an IBM T42. I thought I had an intel chipset wireless card, but the Restricted Drivers list informs me that I have the Atheros Hardware Access Layer driver installed. After some research I *think* I have the Atheros AR5212 card on my system.

The card seems to work fine except I can't log into my home network (I haven't tried at my school yet). 

Some details:Is there anything
I use a D-Link DI-524 wireless router. 
I use an 128 ASCII WEP code for access, and I do not broadcast my SSID.

I can connect without the security features turned off. Weird, eh?

So, what could be the problem?
Is there any simple way, especially for a total noob, to fix/solve this?

I've searched the forums, searched on google and tried to find answers on my own but I give up . . . and would love some help.

Thoughts? THANKS!!!

---

### Post by bonestonne on 2007-10-14
well, i personally use a Netgear WG111v2, and have had great success with it.

i have a T22, so that might/might not matter to you...i had to find another wireless adapter as i don't have internal.

well, when i plug in, i can set it to roaming, or i can specify a network to connect to. when you specify a network, you need the name of the network, password, and its type, DHCP, or specify your IP etc. on roaming, it will normally connect to the strongest signalled open network around, but at the same time, you can also choose "connect to other network" from the menu on the icon for wireless.

when i set my home wireless up, i made a keyring for it, so i just enter the keyring password upon startup/whenever i plug in the adapter and it connects automatically.

i'm pretty sure that you should be able to configure the network the same as i did regardless of the adapter, it worked the same way on my Linksys WPC11v3, however that adapter is much weaker, and doesn't pick up my home network half the time.

hope you have luck with that, and FYI, i never used the windows driver with ndiswrapper, i just had an easy plug 'n' play install for linux.

-bonestonne

---

### Post by carolinamagi on 2007-10-16
Ok, so after the new update from yesterday I can can wifi at my house, which is great.
I can't get wifi on my campus. :confused:

UNC uses a 64 bit HEX WEP 

I can log into networks without security settings, my home network (which uses 128 ASCII WEP) but not on campus.

UNC doesn't "support" linux and won't answer questions for it (read: the students who work in the tech department aren't trained for this) and can't help. The irony . . . linux is used on UNC servers. HA!

Oh well.

Thanks!!!

---

