---
title: "network connection setup"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by rudi009 on 2009-02-07
I have just installed ubuntu and need help in setting up a new connection to connect to the internet. in windows I use a ppoe connection;it requires a username and password to connect.help??

---

### Post by tommcd on 2009-02-07
Ubuntu comes with **pppoeconf** installed. To set up your pppoe connection run **sudo pppoeconf** and follow the prompts.

Is this a DSL pppoe connection? Your DSL modem may have the ability to set the user name and password directly into the DSL modem / router's configuration. This way the connection is always on, like a cable modem. You then no longer need to use pppoeconf to connect. The pppoeconf should work for you though.

---

### Post by rudi009 on 2009-02-07
it is a dsl connection but i have no idea about the the automatic thing you are talking about.

---

### Post by tommcd on 2009-02-07
> **rudi009 said:**
> it is a dsl connection but i have no idea about the the automatic thing you are talking about.

You would have to consult the DSL modem's manual. When I first started using Ubuntu I was using Verizon DSL. I first used **pppoeconf** to connect. Then I found out that I could enter my user name and password directly into the Westell DSL modem by typing 192.168.1.1 into a web browser. This got me into the router's configuration so I could enter the user name and password. Google for the manual for your brand of DSL modem, or ask your ISP's tech support to find out if your modem can be setup this way.
See the posts by Physcsdrk in this thread for more info on the Westell DSL modems:
[http://ubuntuforums.org/showthread.php?t=196097](http://ubuntuforums.org/showthread.php?t=196097)

In the meantime, run **sudp pppoeconf** to setup your DSL pppoe connection.

---

