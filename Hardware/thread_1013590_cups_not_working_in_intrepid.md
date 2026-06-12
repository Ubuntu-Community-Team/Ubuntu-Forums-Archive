---
title: "cups not working in intrepid"
date: 2008-12-17
forum: Hardware
---

### Post by RabidWeezle on 2008-12-17
(This is ubuntu not edubuntu sorry)

Hello, I just upgraded my in-law's pc to intrepid and noticed later that their printers aren't working. Turned out to be cups wasn't running. So I check in /etc/init.d/ for cupsys and there was none. So I made a symlink to cupsys and ran it like

```
sudo /etc/init.d/cupsys
```

and voila, the printers worked again. Now I left them to their pc again and I get a call that they rebooted the pc and the printers aren't working again, and cups isn't running. What can I do to ensure that cups runs, and has there been a patch for cups for intrepid so it will load correctly when the system boots. Before this update the printers and cups ran fine, so I don't see what the problem is really. Anyway, thanks for any help.

---

