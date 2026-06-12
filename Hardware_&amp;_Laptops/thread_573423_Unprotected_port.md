---
title: "Unprotected port"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by MachODDO on 2007-10-11
I am an absolute novice to Linux and Ubuntu, which I have installed and love. In checking the efficiency of the installed Firewall, using "ShieldsUp", it was found that port 23 (Telnet) was unprotected. The recommendation was to close this port. Can anyone help, please?? Step by step, please??

---

### Post by Linicks on 2007-10-11
First, are you running telnetd?

To see:

> ps ax | grep -i telne

will show.  If you are not running a telnetd service (I don't think so!), even though port 23 is 'open', nothing can happen as there is nothing to answer to!

The only thing an open port will do if no service on _that_ port is running is show the machine is there.

So, best thing is to install 'firestarter' using synaptic package manager.  That will run draconian IPTABLES rules and close all ports for you.

Lasty, don't use GRC 'shields-up' - that is a pretty poor and loathsome page that is designed to frighten the user.

I use:

[http://www.hashemian.com/tools/port-scanner.php](http://www.hashemian.com/tools/port-scanner.php)

Nick

---

