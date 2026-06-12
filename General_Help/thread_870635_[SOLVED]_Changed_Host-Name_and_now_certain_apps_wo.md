---
title: "[SOLVED] Changed Host-Name and now certain apps wont load."
date: 2008-07-26
forum: General Help
---

### Post by spen25 on 2008-07-26
Running Hardy and I decided to change my computer's host name and now some application ie Update manager/Synaptic won't load from Gnome only when I go into a terminal. Never had this happen before. I also tried the same name change on a separate PC and got the same results. Any Ideas would be greatly appreciated.

---

### Post by AaronLS on 2008-07-26
I'm no linux expert, but being a programmer I bet there's some settings files that have your old host file in them.  I think you could find some utility on linux to search all your files for the old hostname and see what comes up.  Might pop up alot in some logs though, but maybe you'll find something that appears to be settings related that is the culprate.

---

### Post by plucky on 2008-07-26
You also need to change your hosts file ```
cat /etc/hosts
``` so that 127.0.1.1 is the same.

Good Luck

---

### Post by spen25 on 2008-07-26
Hmm not sure, but it appears to be tied to any program that requires me to enter my root password before the application launches. It hangs on the "starting administrative application" Maybe tied to gksu?

---

### Post by spen25 on 2008-07-26
> **plucky said:**
> You also need to change your hosts file ```
cat /etc/hosts
``` so that 127.0.1.1 is the same.

Good Luck

Thanks!

---

