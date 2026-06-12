---
title: "A little problem with &quot;Terminal&quot;"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by ElementEighty on 2009-02-01
Hi everybody.I`m with ubuntu 8.10 for soon and i have a little problem with a terminal.Sometimes when i write some comand it write this 

"E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

What i need to do to remove this problem .. 
If somebody understand that,please help.

---

### Post by MarblePanther on 2009-02-01
That sounds like you are trying to apt-get install something when you already have Synaptic Package Manager or Update Manager open.

That error is caused when you have two instances of a package manager running. You can only have one at a time.  If you want to apt-get, don't have synaptic open, etc...

---

### Post by ElementEighty on 2009-02-01
omg .. :D thanks :)

---

### Post by MarblePanther on 2009-02-01
No Problem!

---

