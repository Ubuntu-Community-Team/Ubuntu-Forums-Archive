---
title: "Controll Ethernet (blink)lights  .. where are the gurus?"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by honeydew on 2008-04-02
I have a server with a number of Ethernet cards and it would be very useful to be able to turn the link lights on, for a particular interface so I can go through and label them.  I have done this before in redhat and on suse.. but I cant for the life of me remember the commands todo this.  All I want todo is make the Ethernet lights blink for a particular interface.. some guru should know this..

---

### Post by honeydew on 2008-04-08
bump!

---

### Post by honeydew on 2008-04-11
well incase anyone is interested in doing this at some point.. 

```

ethtool -p ethX

```

that command will do the trick =]

---

