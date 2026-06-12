---
title: "Upgrade to 9.10 Not Appearing in Update Manager"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by yoggit on 2009-10-29
Hi, I don't get the option to upgrade from 9.04 to 9.10. Update manager just says I'm up to date!

Have tried numerous repositories (including the main server), have 'Normal releases' selected in Synaptic Package manager --> Updates.

No idea why it doesn't work!!

pls help.

Cheers,
Jon

---

### Post by overdrank on 2009-10-29
Hi and welcome, have you tried 
> To upgrade from Ubuntu 9.04 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes)

---

### Post by yoggit on 2009-10-29
Yep - tried that... many, many times with different repositories.

---

### Post by overdrank on 2009-10-29
> **yoggit said:**
> Yep - tried that... many, many times with different repositories.

Ok what is the output of the command in the terminal
```
lsb_release -a

```

---

### Post by yoggit on 2009-10-29
jon@jon-vbox-jaunty:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty
jon@jon-vbox-jaunty:~$

---

### Post by Mutt77 on 2009-10-29
Put your settings in the update manager to normal upgrades not just LTS or never.

---

### Post by yoggit on 2009-10-30
That's the forst thing I did.

I have been getting regular updates and assumed that I'd see the 9.10 update when it was released.

Everything I read says that I have it all set up correctly. I'll try again another day.

---

### Post by JOHNNYG713 on 2009-10-30
Hi I found this link
[http://www.google.com/url?sa=t&source=web&ct=res&cd=4&ved=0CBUQFjAD&url=http%3A%2F%2Fwww.ubuntu.com%2Fgetubuntu%2Fupgrading&ei=5bLqSoTVBY6EMuivvY0G&usg=AFQjCNFBdtwJFAb7lVHrGB6hUiWkhjjyPQ&sig2=iH5pICabcmBBXFyKEwAXVg](http://www.google.com/url?sa=t&source=web&ct=res&cd=4&ved=0CBUQFjAD&url=http%3A%2F%2Fwww.ubuntu.com%2Fgetubuntu%2Fupgrading&ei=5bLqSoTVBY6EMuivvY0G&usg=AFQjCNFBdtwJFAb7lVHrGB6hUiWkhjjyPQ&sig2=iH5pICabcmBBXFyKEwAXVg)

---

### Post by yoggit on 2009-10-30
Well, I came home, removed the proxy setting and HAZZAH - **It now works**.

I presume it's *supposed* to work via a proxy....???

---

