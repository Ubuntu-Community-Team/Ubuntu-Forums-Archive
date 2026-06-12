---
title: "After install updates damage modules"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by abiezerm on 2005-06-02
hi,

i'm new in ubuntu distro, and after install updates in my desktop pc ubuntu doesn't recognize my network card and sound card.

what can i do??

thanks.

---

### Post by alastair on 2005-06-02
Take each problem at a time - and explain the problem a little more.

Check the system logs i.e. look at the logs from the last boot :

/var/log/syslog

and see if the network device appears (eth?, driver etc.), or any errors.

Also - output of :

ifconfig -a

---

