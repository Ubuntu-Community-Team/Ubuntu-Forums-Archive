---
title: "Lenovo V460 broadcom b43 wifi flaky on maverick 10.10 worked in lucid 10.04"
date: 2010-10-20
forum: Hardware
---

### Post by stevefranks on 2010-10-20
Lenovo V460: wifi worked fine in 10.04, except it wouldn't connect to 802.11N networks.  I upgraded (wipe & fresh install) to 10.10, and now the wifi is junk;  it will drop out after 15 minutes and not come back, and if you suspend/resume, it goes away immediately and irreversibly.

I tried changing networkmanager to wicd, with zero effects, and I also followed several posts and added "b43" to SUSPEND_DEVICES (or something along those lines) in /etc/acpi-something-or-other (hard to recall when the machine won't connect to the net, after all - firefox can't reload my reference pages).

Just as an FYI, I've been a freebsd+xfce guy until last month (wow I love apt), so I'm pretty familiar with how/why stuff works in ubuntu, but all your config files & utilities have different names & locations; you might have to pretend I'm dumb if you have suggestions :(

Thanks!
Steve

---

