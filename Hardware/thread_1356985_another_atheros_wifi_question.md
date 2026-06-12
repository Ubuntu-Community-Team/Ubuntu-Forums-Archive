---
title: "another atheros wifi question"
date: 2009-12-16
forum: Hardware
---

### Post by iThingy on 2009-12-16
I have the acer aspire 5517 with an Atheros AR5B95 running in Ubuntu 9.10

The wifi works fine when I browse the web, but when I use it with torrents, skype, and large file transfers between my laptop and PC the connection fails and I am disconnected from my router. I'm asked me to authenticate and sometimes it will not reconnect without a system restart.

Everything works fine in windows 7. Is there a solution to this problem?

---

### Post by NKK on 2009-12-29
Having similar problem with eMachine E525 (acer brand with Atheros AR5B95).

All works well with Vista but I'm not going to use it ;)
I'm using 9.10 i386, wanted to try AMD64 but it did not find any network devices during installation.

---

### Post by jml on 2009-12-29
The problem is probably related to the driver for the card.  This Atheros chip set supports 802.11n and is a relatively new chipset.  Linux support for new hardware often lags a bit. I had a similar problem with a netbook using a different chip set.  what I found to work as a temporizing measure while I waited for an updated driver to become available was to move physically closer to the wireless access point. Not a perfect solution, but it got me by until the new driver arrived.

Joe

---

