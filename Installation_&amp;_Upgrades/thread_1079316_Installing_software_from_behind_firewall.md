---
title: "Installing software from behind firewall?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by strife242 on 2009-02-24
Sorry about the title for being a little bit nondescriptive but I will attempt to clarify the problem a bit below:

I'm running Intrepid on one of my boxes at home, this box access the Internet through a Clavister firewall and all is working as intended until I enable the HTTP ALG (Application Layer Gateway) feature of this firewall, which I find quite useable due to the fact it supports real-time antivirus protection and mime type verification amongst a few other things.

This makes upgrades (or any kind of download) from the repositorys fail with timeouts and I think this is due to HTTP pipelining and the lack of support for the same in the firewall.

Basically I have two questions:

Does anybody happen to know where I can read up on how the procedure works?

Is there anything I can do to change the standard way of using packages at all, basically not using the pipelining functions?

---

### Post by strife242 on 2009-02-27
I managed to solve this myself.

I added the following:
Acquire::http::Pipeline-Depth "0";

in /etc/apt/apt.conf.d/01ubuntu

Works like a charm.


the smiley is a : followed by a P in case you missed it..
Kind of stupid to even use smileys like that on a forum where I'd guess people post as above quite frequently?!

---

