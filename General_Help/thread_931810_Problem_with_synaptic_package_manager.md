---
title: "Problem with synaptic package manager"
date: 2008-09-27
forum: General Help
---

### Post by miwags on 2008-09-27
Being a newbie to Ubuntu I have found synaptic package manager to be superb. Until today! I installed some updates that came in this morning (27Sept08). After this instal, when I try to open synaptic package manager I get:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
so the stupid question is -- how do I do this?
thanks
Mike

---

### Post by Xiong Chiamiov on 2008-09-27
[Open a terminal]("http://www.psychocats.net/ubuntu/terminal") and run
```

sudo dpkg --configure -a

```

---

### Post by miwags on 2008-09-27
Thank you, that and then a repair of broken packages fixed it

---

