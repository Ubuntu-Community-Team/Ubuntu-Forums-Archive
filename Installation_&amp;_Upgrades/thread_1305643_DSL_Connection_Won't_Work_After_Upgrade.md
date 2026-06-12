---
title: "DSL Connection Won't Work After Upgrade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by bbqsauced on 2009-10-30
So I upgraded to 9.10, and there didn't seem to be too many problems.  (Is there supposed to be sound on the splash screen now?)

Anyhow, I have a Verizon Online DSL connection, and have been using it successfully with my previous versions of Xubuntu for quite some time.

I upgraded, and it can't seem to connect at all.  I played around with the settings, and nothing I did seemed to work.  Tried restarting the modem and all that jazz.

It works in Windows still, so it's definitely an issue with the upgrade.

---

### Post by eyal_allweil on 2009-11-03
You can try the suggestion described here:

[http://ubuntuforums.org/showthread.php?t=1306053](http://ubuntuforums.org/showthread.php?t=1306053)

It's to add the ppa here which has a fixed version of Network Manager. Some people are saying to uncheck "available to all users" in order to make it work.

[https://edge.launchpad.net/~network-manager/+archive/trunk](https://edge.launchpad.net/~network-manager/+archive/trunk)

I'll try it tonight when I get home.

Good luck!

---

### Post by tommcd on 2009-11-03
> **bbqsauced said:**
> S
Anyhow, I have a Verizon Online DSL connection, and have been using it successfully with my previous versions of Xubuntu for quite some time.
I upgraded, and it can't seem to connect at all.  I played around with the settings, and nothing I did seemed to work.
What are you using to connect to the DSL modem? Are you using **pppoeconf**, or network manager? Or is your DSL modem set to automatically connect to the internet?

What Verizon DSL modem do you have? Most modern DSL modems, like the Westell modems that Verizon uses, will allow you to set your Verizon username and password directly into the modem's configuration. This way the DSL connection is always on, like a cable connection. This way no software is needed to connect to the DSL modem since it is always on.
See the posts from Physcsdrk in this thread for how to configure the DSL modem with your username and password:
[http://ubuntuforums.org/showthread.php?t=196097](http://ubuntuforums.org/showthread.php?t=196097)
See posts #16 and 20 in that thread.

---

