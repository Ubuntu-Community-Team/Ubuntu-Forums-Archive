---
title: "NTP protocol over wireless"
date: 2008-10-14
forum: General Help
---

### Post by johnny42 on 2008-10-14
I'm having a problem with the NTP service. I have it configured to poll 6 servers and it works fine on a wired connection but when I move to a wireless network the servers become unreachable.
I was wondering is it the particular network or is there something associated with the ntp service I have to configure in order for it to work over wireless?

Thanks for any help

---

### Post by iponeverything on 2008-10-14
> **johnny42 said:**
> I'm having a problem with the NTP service. I have it configured to poll 6 servers and it works fine on a wired connection but when I move to a wireless network the servers become unreachable.
I was wondering is it the particular network or is there something associated with the ntp service I have to configure in order for it to work over wireless?

Thanks for any help

The protocol is not aware of your connection type. I think that it is something particular to the wireless network your attached to. Perhaps there is some type of filtering going.

---

