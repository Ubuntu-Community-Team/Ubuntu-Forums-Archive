---
title: "Jaunty and Hdparm.conf"
date: 2009-05-22
forum: Hardware
---

### Post by cmcginty on 2009-05-22
Does Jaunty run the hdparm.conf file during startup? Is there a script to manually execute this file? The manpage does not seem to indicate how to actually "use" hdparm.conf.

Where should I put my hdparm settings if hdparm.conf is not the right location? Is this documented anywhere?

[Solution]
These days most of the hdparm settings seem to be done by udev see /lib/udev/rules.d/85-hdparm.rules. That rule calls this script /lib/udev/hdparm which seems to read the hdparm.conf.

---

### Post by capscrew on 2009-06-01
> **cmcginty said:**
> Does Jaunty run the hdparm.conf file during startup? Is there a script to manually execute this file? The manpage does not seem to indicate how to actually "use" hdparm.conf.

Where should I put my hdparm settings if hdparm.conf is not the right location? Is this documented anywhere?

```
man hdparm.conf
```

---

### Post by cmcginty on 2009-06-01
Next time read the original post. I already said the man page does not provide any of this info.

---

### Post by capscrew on 2009-06-02
I did read the original post.  You indicated that you had read one of the pages.  There are two man pages.  One for hdparm and one for hdparm.conf.

Read 'em both!

---

