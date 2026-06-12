---
title: "Opensync fails at Calendar 0x80072F78"
date: 2008-12-02
forum: Hardware
---

### Post by Hooya on 2008-12-02
Contacts sync fine, synce-pls shows files just fine.

When I attempt to do a sync it gets through my contacts, then the device stops at the Calendar stage with the error code.  The terminals continue on as if it were still processing properly.  The last output for the sync command is:

```
Member 1 of type synce-opensync-plugin just disconnected
All clients have disconnected
The sync was successful
DEBUG:SynCE:finalize() called
```

Ironically not true, as the sync was not successful.

Output of the engine looks totally normal.

I used to have things working great, then the Calendar just stopped syncing.  I've rebuilt the whole sync partnerships and I still have the problem.

Any ideas?  What's going on here?  Why does it just fail at the Calendar?

---

### Post by megandy on 2009-03-07
Same is here using a Palm Treo with Windows Mobile 6.1. When I trigger a sync from the mobile a short message appears showing something like syncing Calendar 0/370 and stops then. But no Calender entries have been synced.

Have you managed to get ToDo and Notes working? At my side only syncing of Contacts works.

---

