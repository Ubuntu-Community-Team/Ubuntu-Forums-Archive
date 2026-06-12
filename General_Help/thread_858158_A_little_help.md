---
title: "A little help"
date: 2008-07-13
forum: General Help
---

### Post by root-x on 2008-07-13
in Ubuntu do i need a firewall or a anti virus or not ... cause i did a port scan and my ports are stealth-ed so do i have it built in or not or ain't virus , ain't viruses made for Linux ?  +  how do i spoof my ip and use a dns server or proxy server for all my connections e.g when im using root terminal also know in windows as (cmd) .

+ how do i install the tracert command i have installed nmap using : apt-get install nmap + when i copy it says ( cannot post don't have the permission ) how do i get the coopy-paste permission also 

sorry for the n00byish questions ... ( i aint a n00b with windows thou lol )

---

### Post by pofigster on 2008-07-13
There's already a firewall built into Ubuntu through iptables.  You can install a program called firehol which will allow you to change settings and what not, but that's 100% optional.

You do NOT need anti-virus for Linux right now.  While viruses do exist, they're not floating around the 'net like they are for other OS's.  However, if you're super concerned, you can install ClamAV and get some scanning software out of Synaptic that will scan for viruses.

I'm sorry, but I don't know how to spoof IP addresses...

---

### Post by cyclobs on 2008-07-13
well i believe ubuntu has a built in firewall working in the background. but as for anti-virus it's not really needed. since there is very little viruses for linux and even then very little of them even work now.

and what do you mean byy spoof your ip address?

---

### Post by cyclobs on 2008-07-13
(oops, pressed the button too many times)

---

### Post by Kevbert on 2008-07-13
The only reason for needing an antivirus is if you're either emulating or sharing files with windows.  You'll be very (very) unlikely to get a native linux virus, but you could get a dos virus if say you use DosBox. These viruses will not effect linux.  ClamAv (antivirus) will only find dos viruses.  I don't know about Avast.

---

### Post by WRDN on 2008-07-13
As others have said, a firewall is built in, and nothing is listening on the ports so you don't have to worry about that.
As for anti virus, the majority of viruses are written for Windows, and unlike Windows, something in Ubuntu cannot run and affect the system or others files, without getting over a lot of hurdles first. I would keep an on-demand anti virus program installed so you have it there. I use ClamAV. If you share files with Windows computers, its worth scanning files so you don't pass a virus onto someone else.
Finally, regarding proxies, they are easy to setup. Just select System > Preferences > Network Proxy and you can enter the information there. This will be used for all connections.

---

### Post by root-x on 2008-07-13
thanks for the info all sorted now ... 

i found the trace route e.t.c and other commands in the network tools sections so thats sorted.

---

### Post by Uchiha_madara on 2008-07-13
> **root-x said:**
> in Ubuntu do i need a firewall or a anti virus or not

My Dear Root-X ,
the Viruses cannot infect Ubuntu , However

1 - Open Add-remove Applications from the Application Menu
from The Left Menu : Programming, Games , Education, choose System tools"I think"

2-  click on it , then Look for "Virus Scanner"
Install and enjoy

There is a thread , talks about the Risks :

[http://ubuntuforums.org/announcement.php?f=331](http://ubuntuforums.org/announcement.php?f=331)

I hope that's  help you

sincerely

madara

---

### Post by root-x on 2008-07-13
thanks ...

---

