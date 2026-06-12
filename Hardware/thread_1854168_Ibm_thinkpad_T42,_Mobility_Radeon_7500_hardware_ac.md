---
title: "Ibm thinkpad T42, Mobility Radeon 7500 hardware acceleration 11.04"
date: 2011-10-03
forum: Hardware
---

### Post by auto123 on 2011-10-03
I want to enable hardware acceleration for my R100 ati chipset, which does look plausible for older versions of ubuntu that use Xorg.

[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

I've read to create/configure an Xorg.conf I could use 

```
sudo Xorg -configure

```but whenever I try that, I get an error that says:

```
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.
```So, I'm confused here, is it possible to use Xorg in the newest ubuntu 11.04 or configure this gpu to work?

---

### Post by Mark Phelps on 2011-10-04
Looks like that Wiki was written back in the Hardy Heron 8.10 days -- which, back then, did provide restricted driver support for what are now considered "legacy" cards.

But those drivers will not work with any recent Ubuntu versions -- and nothing you can hand-bash into an Xorg config file is going to make that happen.

The open-source drivers, which are installed by default, are the only ones that will work with your card now.

---

