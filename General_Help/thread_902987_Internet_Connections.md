---
title: "Internet Connections"
date: 2008-08-27
forum: General Help
---

### Post by dudude on 2008-08-27
My questions is about how most Linux distributions, or even operating systems manage multiple connections to the internet.

If I were to have a computer on a wired connection to the internet, and a wireless connection to a different internet connection, what would Ubuntu do with these connections.

Would it just ignore the new connections, use both connections simultaneously, use the fastest, or ?

I would Google this, but I do not know what to search for in the first place:)

---

### Post by Bucky Ball on 2008-08-27
[http://www.computing.net/answers/networking/simultaneous-wireless-and-hardwire-/13613.html](http://www.computing.net/answers/networking/simultaneous-wireless-and-hardwire-/13613.html)

That might be of some help. Have you tried it anyhow? This page is suggesting setting up something like a different IP for each connection probably in your router. The best place for this thread is in the Wireless and networking forums here: 
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

You will get more specific help.
Good luck. :)

---

### Post by iaculallad on 2008-08-27
The OS should prioritize who comes first based on the order of connections. This is what happens when I plug my wired connection while my wireless connection is active, the OS switches on using wired connection silently because it's got priority over the wireless connection.

EDIT:

> My Wired has an IP of 192.168.5.6 and Wireless connection has .7. Both using different private IP address

---

### Post by dudude on 2008-08-27
Thanks for the fast replies!

Just one more think I would like to know is if it is possible to download a file or something with both internet connections simultaneously with a program like aria2, or is there a one connection limit for a computer?

---

### Post by iaculallad on 2008-08-27
> **dudude said:**
> Thanks for the fast replies!

Just one more think I would like to know is if it is possible to download a file or something with both internet connections simultaneously with a program like aria2, or is there a one connection limit for a computer?

That would be possible but it would require you to do routing configuration work before you could attain a load balancing between the two connections. I got not answer about aria2 since I do not use it myself.

---

