---
title: "PB laptop hangs at boot-up"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by fsckme on 2007-10-01
Hi all. I installed the public Gutsy beta on my mothers(!) laptop recently, and it worked fine a couple of days. Then - all of a sudden - it stopped booting. The laptop is a Packard Bell EasyNote R6727 D (fooled by a clever salesman, it was even more expensive than my MacBook with extra specs!) with Intel 2200 wireless chipset. I'm not able to boot in recovery mode either, the whole process hangs under "loading manual drivers". I'll list every action in this section:

* Loading manual drivers
lp: driver loaded but no devices found
ipmi message handler version 39.1
IPMI system interface driver
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
ADDRCONF(NETDEV_UP): eth1: link is not ready

*insert at least 30 minutes here*

ipmi_smic_drv: smic hosed: smic timed out
IPMI BT: timeout in XACTION [ B_BUSY H_BUSY OEMO SMS H2B ] 1 retries left
IPMI BT: timeout in XACTION [ B_BUSY H_BUSY OEMO SMS H2B ] failed 2 retries, sending error response
IPMI: BT reset (takes 5 secs)
IPMI BT: timeout in XACTION [ B_BUSY H_BUSY OEMO SMS H2B ] failed 2 retries, sending error response
IPMI: BT reset (takes 5 secs)
IPMI BT: timeout in XACTION [ B_BUSY H_BUSY OEMO SMS H2B ] failed 2 retries, sending error response
IPMI: BT reset (takes 5 secs)


...this just loops endlessly (although with different code-prefixes). And takes a LOT more than 5 seconds before the next message, more like 20 minutes.

Unfortunately, I don't know exactly what I did before this started happening, because it was on a few days in a row and I played around with a lot of things (although nothing I haven't done before successfully). But I'm certain that it happened after a short Windows-boot on the same computer.

Windows and Ubuntu booted fine a good couple of times before this happened. Does anyone have any idea of what to do? She was bothered a lot with spyware, and I just convinced her to give Linux a shot using all the arguments there is, and a little more. This is a major setback in a lengthy process :-|

---

