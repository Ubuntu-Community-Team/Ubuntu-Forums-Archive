---
title: "Laptop shutdowns suddenly!"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by xp_newbie on 2006-06-16
[Actually the title should be: LAPTOP TURNS OFF ABRUPTLY]

I was in the middle of reloading available package list in Synaptic, when all of a sudden m laptop (Lenovo 3000) shut down on me. I wasn't even touching any mouse or keyboard when this happens.

When I touched the laptop (while still off) it was **[SIZE="2"]hot[/SIZE]**.  Very hot.

Apparently, the drivers/circuits that are responsible for automatically controlling the CPU temperature  (ACPI?) simply did not function. This problem does not exist when running Windows XP SP2 (dual boot install on this laptop).

How do I start looking for a hint that will allow me solve the problem?

Am I missing a driver?
Do I need to configure something?
Or is it simply a bug in the kernel that I have to wait for it to be fixed?

Thanks!
Alex

---

### Post by emenny81 on 2006-06-16
yes I would stop using ubuntu if I was you, laptop could one day use not turn on :D

---

### Post by xp_newbie on 2006-06-17
[QUOTE=emenny81]yes I would stop using ubuntu if I was you, laptop could one day use not turn on :D[/QUOTE]

I guess this the kind of an answer I should expect when there is no solution to the problem? :( 

In the meanwhile I upgraded the kernel to 2.6.15-25-686.

The sudden and abrupt shutdown hasn't occurred again (yet), but the laptop fan is constantly ON which means that something in the thermal control of the system is not working properly - under Ubuntu. Under Windows XP there is no such problem.

Any idea how to solve the problem? Clearly I am not the first one running Ubuntu on a laptop, right?

I truely hope this only needs some user config like in System > Preferences > Power Management. Otherwise I am afraid the advice given by the only replier to this post could turn out to be the most helpful one.  :(

---

### Post by xp_newbie on 2006-06-18
Well, I think I just discovered what's causing this CPU overload: I used the command line 'top' to see what's consuming so much CPU and discovered that there is some bacground program (daemon?) running - one instance **per each** time I pressed "Print Screen" or "Alt + Print Screen".

Anyone knows more about this rogue "snapshot" program? Why is it behaving like this and what can I do to solve the problem?

Also, there is a fundamental problem in Linux if a 100% CPU load eventually leads to an abrupt turn-off of the laptop instead of orderly shutting down the system. I have never experienced anything like this on Windows 2000/XP and I know that Linux is a much better designed system. How come this problem exists?

BTW, this is not the only laptop I have seen this problem happenning with - and not the only Linux distribution. I saw this problem (or abrupt turn-off, losing all current sessions and their associated data modifications) on a Compaq Armada running FeatherLinux too.

---

