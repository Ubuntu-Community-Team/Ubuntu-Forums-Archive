---
title: "DBUS in Gutsy suspends, wakes up, then hibernates"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by frogotronic on 2008-04-02
Hi,

   Gutsy Gibbon (7.10) all updates applied.  Got a weird problem - might be DBUS related, but I think I might fix it at the level of the GPM config file.  When I have "Put computer to sleep after 1 hour" on AC power selected, the machine is suspended (not hibernated).  Upon waking up from suspend everything is normal, but the machine immediately hibernates.  Then resume from hibernation is totally fine.

   This is claimed to be a [ DBUS error]("https://bugs.launchpad.net/ubuntu/+bug/181729"), but I was wondering if this is a GPM issue which essentially calls the "wrong" action?  I.e.  Is it suspending, and then hibernating?  If so, can this be fixed/modified at the level of the GPM config file to just hibernate?

I really haven't mucked with anything like this before.

Q)  Is it possible to patch DBUS, without upgrading to Hardy?

Q2) How likely is it that this is a GPM config error?

- CH

---

