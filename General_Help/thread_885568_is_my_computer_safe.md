---
title: "is my computer safe"
date: 2008-08-10
forum: General Help
---

### Post by pc_doc on 2008-08-10
I have set up my router so that i can use transmission to download torrents i have followed the instructions on portfoward.com
But when i go to ShieldsUP web site it tells me my ports are closed and not Stealth is this safe can anyone get in to my computer.

---

### Post by Vivaldi Gloria on 2008-08-10
> **bodhi.zazen said:**
> "Stealth" is a bad term.

See this link :

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Table_14-2_Descriptions_Of_The_Most_Commonly_Used_Targets](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Table_14-2_Descriptions_Of_The_Most_Commonly_Used_Targets)

The options are "Reject" and "Drop"

Reject sends an error message, drop does not. Most people feel they are equal in security (security through obscurity is no security), although opinions vary.

Thus "stealth" == "drop" and a close port is as secure as a stealth port, you are worried about open ports or the "accept" option (unless you are running a public server ...)

from

[http://ubuntuforums.org/showthread.php?t=874899](http://ubuntuforums.org/showthread.php?t=874899)

So, yes, your computer is safe.

---

### Post by lukjad on 2008-08-10
Also, if you really care about security, you may wish to try Nbuntu, a variant of Ubuntu that is made specifically for security.

---

### Post by hyper_ch on 2008-08-10
what does nbuntu do differently?

In the end, by default ubuntu is very, very secure... however adding stuff like bittorrent clients, webservers, .... you open more attack vectors.

---

