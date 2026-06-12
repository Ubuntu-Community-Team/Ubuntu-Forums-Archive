---
title: "[SOLVED] NFS refuses to share directory"
date: 2008-07-31
forum: General Help
---

### Post by sebrock on 2008-07-31
I have a ubuntu server that has been everything from 6.06 to 8.04.1. Now I have a few NFS shares on that server. It has never been any problems until now.

syslog:
```

mountd[5212]: refused mount request from 192.168.0.4 for /var/Files/500GB (/): not exported

```

from client (showmount -e nfs.server)
```

Export list for 192.168.0.3:
/var/Files/250GB                 192.168.0.*
/var/Files/200GB                 192.168.0.*
/var/Files/500GB                 192.l68.0.*

```

so its marked as exported at the server

Right now I have three shares exported:

```

/var/Files/500GB      192.l68.0.*(rw,async,insecure,no_subtree_check,all_squash,anonuid=501,anongid=1000)
/var/Files/200GB      192.168.0.*(rw,async,insecure,no_subtree_check,all_squash,anonuid=501,anongid=1000)
/var/Files/250GB      192.168.0.*(rw,async,insecure,no_subtree_check,all_squash,anonuid=501,anongid=1000)

```

All works fine except the first one (500GB disk). I should add that this is a new disk which I just installed. It works fine locally on the server and is mounted and everything. The IDs comes from that I also access this from a macbook.

The interesting part is that it has as stated always worked and now suddenly ONE of them doesnt work but the other does.

Im totally clueless and sort of sick with NFS now. It seems to have never ever resolved bugs. Any help here? This is really starting to get ridiculous.

Regards

---

### Post by john.nicholls on 2008-08-01
In the second code block the first entry shows 192.l68 instead of 192.168.
Could this be the problem?

---

### Post by sebrock on 2008-08-01
> **john.nicholls said:**
> In the second code block the first entry shows 192.l68 instead of 192.168.
Could this be the problem?

Of course that was the problem. When you stare at it for hours like I did, you dont see these obvious things... thank god I copy-pasted it and not just wrote it... :D

Now I shall go and throw myself out the window. Thank you very much!
:lolflag:

---

