---
title: "DSL connection problem on Ubuntu 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by giselaez on 2009-11-02
Hi! I upgraded to 9.10 and after that I was unable to connect to the internet. My internet connection is trough a DSL pppOe modem. It was working before the upgrade. 

I run [FONT=monospace]"[/FONT]sudo pppoeconf" and followed the steps to set up the modem, but nothing changed.

Please, I need help with this.

Is there something in the upgrading that can change network settings?

I apologize for my poor English.
giselaez

---

### Post by eyal_allweil on 2009-11-03
You can try the suggestion described here:

[http://ubuntuforums.org/showthread.php?t=1306053](http://ubuntuforums.org/showthread.php?t=1306053)

It's to add the ppa here which has a fixed version of Network Manager. Some people are saying to uncheck "available to all users" in order to make it work.

[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

I'll try it tonight when I get home.

Good luck!

---

### Post by rahul_dhankani on 2009-11-15
hey, i had the same problem. You probably did this but incase you missed it:  after the **pppoeconf** plugin installs, type **pon dsl-provider** to connect. it worked for me.

---

### Post by margemoosh on 2010-01-05
> **rahul_dhankani said:**
> hey, i had the same problem. You probably did this but incase you missed it:  after the **pppoeconf** plugin installs, type **pon dsl-provider** to connect. it worked for me.
yes it workes but what if i want to use network manager and GUI to connect to DSL?

---

