---
title: "Quick question"
date: 2008-08-02
forum: General Help
---

### Post by ecko19 on 2008-08-02
I am new to linux and ubuntu and I recently installed server edition on a extra computer that I had.  I connected it to my router and installed server edition.  I installed ebox on it and i have been playing around with it.  I want to use the server as a "only for my network" file sharing and print sharing.  I don't want it to have any communication to the outside world.  With just default settings is anyone on the outside able to gain access to the server?  I was hoping that because it was behind the router that it was fine.  Can someone give me some guidance on this?

---

### Post by spiderbatdad on 2008-08-02
Being behind a router with no ports forwarded by the router is basically safe. Whatever security risks arise after that are usually user initiated, ie, unsafe web usage.

---

### Post by ecko19 on 2008-08-02
Even if someone from the outside tries to access the server that I am running the router should still block it ... correct?

---

### Post by spiderbatdad on 2008-08-02
Your router has to forward requests to the specific local ip address assigned to your machine. If your router has not been configured to forward those requests, they get blocked. It is probably a good idea to modify the default access credentials of your router.

---

### Post by spiderbatdad on 2008-08-02
[http://www.phenoelit-us.org/dpl/dpl.html](http://www.phenoelit-us.org/dpl/dpl.html)

---

### Post by ecko19 on 2008-08-02
Oh well with respect to the router i definitely changed the pass a long time ago.  The default stuff I am talking about is with ubuntu server and ebox

---

