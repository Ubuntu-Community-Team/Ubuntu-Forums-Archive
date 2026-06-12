---
title: "Asus X51L: no network"
date: 2008-08-15
forum: Hardware
---

### Post by om zanka on 2008-08-15
Just installed ubuntu 8.04.1 to Asus X51L.
And there's no network through Realtek 8139 that's in the laptop.
Even no link lights on a network hub!

Network configured with static local address 192.168.x.y
Ping 192.168.x.y is OK. But can't ping any other IP.

/var/log/messages reports network time outs.

It's OK under MS Windows OS.

Is it improper kernel module loaded for network card?

---

### Post by cdtech on 2008-08-15
Have a look at this post:
[http://ubuntuforums.org/showthread.php?t=91746](http://ubuntuforums.org/showthread.php?t=91746)
It may help you out.........

---

### Post by om zanka on 2008-08-16
> **cdtech said:**
> Have a look at this post:
[http://ubuntuforums.org/showthread.php?t=91746](http://ubuntuforums.org/showthread.php?t=91746)
It may help you out.........

Thank you for your message. But it was another problem.
I've found the solution to mine one!

It seems it's a hardware problem.

Problem case
1) Just turn a laptop on - no link on a network hub
2) Load linux - no link on a network hub still
Result: no network connection.

Solution is to turn network boot on in BIOS.

Solution case
1) Turn a laptop on
2) BIOS tries to boot from network - network link appears!
3) Load linux - all is well
Result: no problem.

---

### Post by cdtech on 2008-08-16
glad you got it solved. thanks for posting your procedure for others to view as well.....

---

