---
title: "Making a Dell Inspiron 6400 with Nvidia GeForce 7300 card go into suspend"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by Laervian on 2007-08-05
Recently it has become evident that when Nvidia drivevr is installed our Ubuntu has some problems for going into suspend (bug #94051). I have just found a workaround, which allows me to go into suspension - but I am not computer savvy and I would like to know if what I did is completely wrong (although it DOES seem to function :) ).

I started from the output of the "sudo hibernate-ram -n" command which both "some drivers failed to unload: nvidia" and errors in the blacklist. What I did then is:

1- modify the /etc/default/acpi-support file and add nvidia to the MODULES_WHITELIST
2- modify the /etc/hibernate/blacklisted-modules file and delete nvidia from the blacklisted list.

Both steps seem necessary as even with nvidia in the whitelist the hibernate script returned an error. Finally, reboot.

Now everything seem to run just fine on my box - suspension has begun to function  again. :D I will try hibernate soon and report the results.

---

### Post by Laervian on 2007-08-05
Hibernation, I am sorry to report, does not function with this workaround. Also, the lid button event is not yet consistent (I know it has hardly anything to do with the problem I think I solved, but I hoped that more consistent suspend could help :) ). But apart from this, suspension now works greatly :D

---

