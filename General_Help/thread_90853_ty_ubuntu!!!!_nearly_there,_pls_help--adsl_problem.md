---
title: "ty ubuntu!!!! nearly there, pls help--adsl problem"
date: 2005-11-15
forum: General Help
---

### Post by trandojedi on 2005-11-15
just wann say taht ubuntu is teh sh!T... like i am soo on the verge of deleting my two windows partitions (i need 2 cause media centre has like a half life of 1 wee kfor ne before format... the otehr 'safe' windows generally goes 2 months without format)... hmmm anyway. the one thing that is stopping me from completely converting to ubunutu is adsl... i posted somethign bout this before... is sorta got it working...

i have like 4 computers connected to a network hub, connected to 1 adsl modem... i have a dynamic ip so that implies DHCP right?? i can connect to adsl with my laptop. this is becuae in the top right hand corner of my screen there is an icon indicating that i have a network card... i then run pppoeconf and everytjhing runs and i'm connected to my adsl. with my desktop that icon is not there. if i go to System -> Admin -> networking my ethernet cards are there. i active the one connected to the adsl and set it as DHCP. i then run pppoeconf but it won't work. :'(

one time i set it to static and put in some value i think i got the value from the DNS tab and then in DNS hosts and ran pppoeconf and i was connected. then i restarted my desltop and it didn't work... but i dont' tjhink this is right.

anyway if anyone could help me out would be appreciated 

garrick, uwa, perth wa

---

### Post by Remmelas on 2005-11-15
if you know a valid IP address for your subnet(ie. one that dhcp would assign anyway), you can specify it as per a static setup, and not use dhcp.  DHCP is not required, but is supposed to be helpful.  I use static setups on my home network to save the trouble of re-arranging my port forwarding ever.  Anyway, not sure I can help with your specific setup, just wanted to make sure that you know you aren't 'required' to use dhcp.  Also, using an ip from your dns didn't work, cuz those are dns servers.  If you know the internal IP address of your dsl modem, a safe bet is to usually add '1' to the last octet, for example, my dsl modem is 192.168.0.1 and I use 192.168.0.2 for my static assigned on this machine, and the other 3 machines on my network just use dhcp

---

### Post by trandojedi on 2005-11-15
ahhh.. ok. with the dsl modem ip address. one time on port forwarding site (even though i don't have a router) i put in one of the addresses and it took to like like a configuration webpage for my modem. is this the ip address i should try add 1 to?

---

### Post by Remmelas on 2005-11-16
sounds like it :-)

---

