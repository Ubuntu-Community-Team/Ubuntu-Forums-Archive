---
title: "Working &quot;Big Desktop&quot; w/ Radeon 9600"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by 73sprint on 2006-04-09
After a long struggle I got a working dual monitor "Big Desktop" setup with my Radeon 9600 under 5.10. Hopefully this will help someone.

I had tried configuring the setup using fglrxconfig while gnome was running without any success. I'm not sure why this worked, but here's what I did:

Backup the xorg.conf
from a bare prompt (no gui running whatsover) I ran fglrxconfig, used all the default settings for Big Desktop. I rebooted and voila. Working Big Desktop.

Is there perhaps some conflict when attempting to configure a dual monitor setup with xwindows already running? Has anyone else seen similar results?

---

