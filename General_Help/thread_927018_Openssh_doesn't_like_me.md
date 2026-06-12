---
title: "Openssh doesn't like me"
date: 2008-09-22
forum: General Help
---

### Post by freebeer on 2008-09-22
I need a little diagnostic help.  I've installed OpenSSH server on my Ubuntu 8.04 box.  From within the LAN I can ssh to the box without problem.  From outside the LAN, I get a connection refused error (I get the same error if using putty on my Winbox and ssh on the Ubuntu box.)  I have forwarded port 22 on my router, and judging from the response and speed of that response, it looks like the request is being forwarded, but is being refused. (ie it doesn't appear to be a port-forward fail, but an outright rejection by the server - but I've been known to be wrong before :D)

I'm not sure how to track this down at this point.

Thanks!

---

### Post by Titan8990 on 2008-09-22
Many ISPs block port 22. I would start by verifying that your ISP is not blocking your connection.

---

### Post by freebeer on 2008-09-22
> **Titan8990 said:**
> Many ISPs block port 22. I would start by verifying that your ISP is not blocking your connection.

hmmm... good point.  I forget that they can do that sometimes.  Thanks!

---

### Post by freebeer on 2008-09-23
Update:  It wasn't the ISP blocking it - it was me.  I didn't configure the router correctly.  :(

---

