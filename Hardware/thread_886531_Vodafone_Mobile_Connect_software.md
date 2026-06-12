---
title: "Vodafone Mobile Connect software"
date: 2008-08-11
forum: Hardware
---

### Post by mpolito1969 on 2008-08-11
Dear all,

I've just bought an ASUS F3Sr notebook, everything works well under Vista but I'd like to move to Linux.

I'm using the Ubuntu (8.04.1) live CD to test for compatibility, At present I can't connect to the internet through the internal UMTS modem.

I ran the Vodafone Mobile Connect software and almost everything was OK: it got automatically configured with my operators data (i.e. the APN), it asked me for a PIN, I gave it, it started and I saw in the bottom of the window appearing the string "Vodafone IT", which means (I guess) it found my operator's network.

I pressed on the "connect" button but nothing happened. No errors shown and no connection established (I could not browse the web with Firefox). The button label didn't change to "disconnect".

I pressed several times the "connect" button but it just didn't do anything.

I ran it again from the command line in the hope I could see some error messages on the console but I couldn'd see anything.

Have you already seen this behaviour? Do you know if there is something like a log file where I can search for error messages?

Unfortunately, I'm using an Ubuntu live CD, which means I'm continously switching between Vista (to connect to the internet) and Linux (to make tests) so troubleshooting the problem is more complicated.

Any help will be appreciated.

Bye,
Max

---

### Post by mpolito1969 on 2008-08-13
Unfortunately there is nothing in /var/log, no file has been updated during my attempts.

If I run 'sudo vodafone-...' and I press on the "connect" button I see a notification windows saying it attempted three times a connection but it couldn't. It suggest there are mistakes in the configuration (but doesn't say anything about where are the configuration files or what options are incorrect) or there is no carrier (I know there is a carrier as I can connect from Vista).

I tried to send an SMS and it worked, I received it on my phone.

I also tried with wvdialconf.

I ran wvdialconf to update the /etc/wvdial.conf file and it made everything without complaining but when I run wvdial it complains the configuration doesn't specify any valid phone number, login name and password. Of course... I don't have any of them.

I don't know what else I could try...

Bye,
Max

---

### Post by mpolito1969 on 2008-09-04
I've found a solution, it's here:

[http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,508/](http://www.pharscape.org/component/option,com_forum/Itemid,68/page,viewtopic/t,508/)

Ciao,
Max

---

