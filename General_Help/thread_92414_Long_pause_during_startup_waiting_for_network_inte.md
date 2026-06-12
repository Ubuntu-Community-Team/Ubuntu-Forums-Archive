---
title: "Long pause during startup waiting for network interface to come up"
date: 2005-11-19
forum: General Help
---

### Post by fergus.b on 2005-11-19
Hi

If I don't have a network cable plugged in during bootup ubuntu takes quite a while trying to bring up the network interface. Is there a way to turn this off and manually do it later or perhaps background the process?

---

### Post by matthew on 2005-11-19
The easiest thing to do is hit <crtl><c> and it will skip that step in the boot process.

---

### Post by cstudent on 2005-11-19
[QUOTE=matthew]The easiest thing to do is hit <crtl><c> and it will skip that step in the boot process.[/QUOTE]

Ha! That's one I knew. Although I just learned it a few days ago. :oops:

---

### Post by Dr. Nick on 2005-11-19
Yeah their is a very similar thread on it aswell

[http://www.ubuntuforums.org/showthread.php?t=92022](http://www.ubuntuforums.org/showthread.php?t=92022)

I personally use the ctrl+c but the dhcp timeout option mentioned may fix it aswell, havent tried it

---

### Post by fergus.b on 2005-11-20
Thanks. I know about ctrl+c but was looking for a way that doesn't require my intervention. I'll have a look at the thread you mentioned Dr. Nick.

---

### Post by Ruso on 2005-11-20
/etc/rc#.d 

#=you  runlevel number. If u are starting in runlevel 3 then it has to be /etc/rc3.d . This directory contains symbolyc links to the services wich has to be started at the boot time. Remove the link to the network service from there. Probably "S05network" file. (The better way is rename changing the capital "S" to the small "s"). It has to solve to your problem I think :))

---

### Post by dcstar on 2005-11-20
[QUOTE=fergus.b]Hi

If I don't have a network cable plugged in during bootup ubuntu takes quite a while trying to bring up the network interface. Is there a way to turn this off and manually do it later or perhaps background the process?[/QUOTE]
If you are using DHCP then it is perhaps a timeout issue waiting for a connection from a DHCP server that isn't there.

You might try a Static IP and see if that helps.

---

