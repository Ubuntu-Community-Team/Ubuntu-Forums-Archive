---
title: "right mouse strange behaviour"
date: 2008-11-02
forum: General Help
---

### Post by brownbear on 2008-11-02
Essentially the right mouse _sometimes_ doesn't do what it's meant to do, and does something which seems random (to me at least).

Sometimes when I right click a hyperlink in firefox, I get the 'bookmark this page' widget.  

Sometimes when I right click a hyperlink in firefox, it opens the evolution mail client.  The time when this happened, I had a terminal open in another virtual desktop with this
```
(evolution:15275): evolution-shell-CRITICAL **: e_shell_set_crash_recovery: assertion `E_IS_SHELL (shell)' failed
Saving 1/1 dirty records of Inbox

(evolution:15270): camel-WARNING **: No summary path set. Unable to migrate


(evolution:15270): camel-WARNING **: No summary path set. Unable to migrate

addressbook_migrate (2.22.0)

```

I've now managed to get it to ask me where I want to save this webpage.

I've also managed to right click a hyper link and it just opens the url in a new window.  

It's infrequent.  I'm trying to reproduce this....


Firefox 3.0.3
Ubuntu 8.10
2.6.27-7-generic
The right mouse button is on a laptop, if that makes a difference...



/edit Ok so these events aren't random, my computer is automatically selecting one of the options on a right click of a url.  Any ideas why it's doing this ?

---

### Post by brownbear on 2008-11-03
I've managed to replicate this behaviour with a mouse plugged into my laptop.

---

