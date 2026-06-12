---
title: "hosts.deny file."
date: 2008-07-26
forum: General Help
---

### Post by StOoZ on 2008-07-26
I use ssh a lot , and also , denyhosts , to prevent brute force attacks.
now , I have couple of blocked ip's in hosts.deny which I removed , but they constantly come back each time I restart the computer, 
how do I prevent this ???

---

### Post by brian_p on 2008-07-26
> **StOoZ said:**
> I use ssh a lot , and also , denyhosts , to prevent brute force attacks.
now , I have couple of blocked ip's in hosts.deny which I removed , but they constantly come back each time I restart the computer, 
how do I prevent this ???

A guess: they come back because the are stored in /var/log/denyhosts.

It is probably best to let denyhosts manage what is in hosts.deny using PURGE_DENY in the configuration file.

---

### Post by StOoZ on 2008-07-27
hmmm I couldnt find any IP in /var/log/denyhosts 

any idea how to remove blockage from denyhosts?

---

