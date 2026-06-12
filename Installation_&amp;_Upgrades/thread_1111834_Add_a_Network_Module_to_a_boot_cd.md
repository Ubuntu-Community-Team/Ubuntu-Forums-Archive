---
title: "Add a Network Module to a boot cd"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by b-boy on 2009-03-31
Hi guys I have a SLES 9 customer server build and I need to add a network module to it I have managed to get the module working once they system is installed But i need to include it in to the cd how do I do this??

---

### Post by cariboo on 2009-03-31
Unless you've got a obscure noname brand nic,or one that is so new that there are no drivers for it, the drivers should be on the install cd. Please paste the output of:

```
lshw -C network
```

in your next post.

Jim

---

### Post by b-boy on 2009-04-01
lshw is not a command on sles 9

---

