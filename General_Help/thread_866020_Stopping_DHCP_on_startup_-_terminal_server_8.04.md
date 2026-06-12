---
title: "Stopping DHCP on startup - terminal server 8.04"
date: 2008-07-21
forum: General Help
---

### Post by NKane on 2008-07-21
Hey everyone. I need to stop DHCP from starting up when the server reboots. I'm running 8.04 without an X environment. What do I need to do? Thanks in advance.

---

### Post by justleen on 2008-07-21
you can use the "update-rc.d" command for this

from the man page: ```

       Example of disabling a service:
          update-rc.d -f foobar remove
          update-rc.d foobar stop 20 2 3 4 5 .

```

---

