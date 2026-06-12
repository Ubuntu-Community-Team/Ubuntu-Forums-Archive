---
title: "standby &amp; Samsung X20"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by aiv on 2006-08-08
it doesn't work since Dapper is out!
The same problem goes for display alone, it doesn't go to sleep.

---

### Post by Moloko on 2006-10-22
I solved this problem adding this lines in the /etc/X11/xorg.conf file:

- In the **Monitor** section

```
Option "DPMS" "true
```

- In the **ServerFlags** section:

```
Option "StandbyTime" "3"
``` ( 3 minutes in my case).

---

