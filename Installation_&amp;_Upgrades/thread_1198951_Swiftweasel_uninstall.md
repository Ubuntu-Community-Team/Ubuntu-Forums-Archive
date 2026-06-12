---
title: "Swiftweasel uninstall"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by TSWMIN85 on 2009-06-28
I'm fairly new to Ubuntu and have a problem.

I downloaded the Swiftweasel 3.0.3 .deb file, installed it, and didn't like it.

Now it's not showing up in the ADD/REMOVE thingy. When I search in Synaptic Package Manager for SWIFTWEASEL nothing comes up.

Can someone help me uninstall this program, in simple terms?

Thanks in advance,
Guy Who Left Windows for Beautiful, Sexy, Ubuntu!

---

### Post by ajgreeny on 2009-06-28
If you searched with upper case I don't think anything will show in synaptic.  Linux is case sensitive, unlike windows.  If that is not the problem and you installed by double clicking the .deb file in nautilus, you can uninstall with the command ```
sudo dpkg -r swiftweasel
```or purge it with ```
sudo dpkg -P swiftweasel
```Make sure you get the package name correct, including the case, but ignore the .deb at the end.

---

### Post by TSWMIN85 on 2009-07-01
Indeed I did it without discretion for cap locks.

Thank you very much.

I'm loving Ubuntu!

Mmmmmmmmmm... OS as sexy as Adrinna Lima...

---

