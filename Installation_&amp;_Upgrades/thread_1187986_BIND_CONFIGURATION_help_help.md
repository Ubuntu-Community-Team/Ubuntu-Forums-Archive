---
title: "BIND CONFIGURATION help help"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by ncnbnt on 2009-06-15
[B]Hello,

i installed bind9.Then i installed plesk.

But plesk doesnt recognise BIND .

How to set it up for plesk?

Thanks[/B]

---

### Post by ncnbnt on 2009-06-15
When putting: rndc start i see:


**rndc: connect failed: 127.0.0.1#953: connection refused**


But named -g all seems ok.

Pleaseeee help

---

### Post by 007casper on 2009-07-02
check the logs

tail -f /var/log/daemons.log 

or

tail -f /var/log/daemon.log

use gadmin-bind from synaptic

---

