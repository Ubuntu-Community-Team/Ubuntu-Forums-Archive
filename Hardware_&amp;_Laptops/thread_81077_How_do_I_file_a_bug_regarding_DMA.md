---
title: "How do I file a bug regarding DMA???"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by daller on 2005-10-23
Hi There,

I've heard that if activating DMA on a CD-drive or a harddisc, only using hdparm and editing /etc/hdparm.conf (not editing /etc/modules) I should file a bug about that the device should have DMA activated as default!

How do I do that?

(I have a bunch of laptops that hadn't DMA activated on the DVD-drive as default - but they work perfectly with it activated!!!)

---

### Post by John.Michael.Kane on 2005-10-23
[https://bugzilla.ubuntu.com/](https://bugzilla.ubuntu.com/)
[https://launchpad.net/](https://launchpad.net/)

---

### Post by daller on 2005-10-23
More specific, what do I file?

...How do I find out what drive I have? (The information the devs will need)

Is it a hdparm "bug"?

---

### Post by John.Michael.Kane on 2005-10-23
hdparm -i /dev/hda

---

