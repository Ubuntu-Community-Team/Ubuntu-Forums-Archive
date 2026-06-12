---
title: "ssh + firestarter ... port 22 incoming allowed... still nada"
date: 2005-11-04
forum: General Help
---

### Post by djlosch on 2005-11-04
i set firestarter to allow incoming port 22 from everyone and outgoing port 22.

i can ssh out fine.  i can even ssh to localhost.  however, when i go over to my laptop on a different network, or ssh into my solaris box at school, and i try to ssh into my home kubuntu box, i get no connection.

i tested to see if sshd was not running, or running on a different port (sshd_config has it on default 22), but i can ssh in both from my laptop and my solaris box when i turn the firewall off.

any ideas what's wrong?

---

### Post by mlomker on 2005-11-04
> any ideas what's wrong?

If firestarter were blocking it then you'd see something in the Event tab.  Are you seeing anything there?

---

### Post by djlosch on 2005-11-04
nothing... but it only happens when firestarter is running with the firewall up.

i even tried deleting the rule.  then ssh in to get the event to show up (and it did).  then add it again via the right click in case i did something wrong.  still no love.

---

