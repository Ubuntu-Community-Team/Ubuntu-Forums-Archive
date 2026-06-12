---
title: "Everything but network works on 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by stanley45 on 2009-11-06
I've been running 9.04 for a while, on a multiboot machine shared with Vista, multibooting via Acronis.  
I did the automatic download, which worked smoothly and quickly.  But when I tried to connect to the internet, Ubuntu told me there was no network.  What to do?
If I multiboot back to Vista, the network works perfectly (and I am using it for this thread).  
I didn't see any other threads with this weird problem.  I tried using the Network Tools, Network Preferences, but didn't see anything there to help.  ?????

---

### Post by stanley45 on 2009-11-07
New info on this weird change in 9.10

On Vista, three networks appear, mine being the strongest and my two neighbors, much weaker.
On Ubuntu 9.04, it was identical, and Ubuntu automatically connected to my home network.
On Ubuntu 9.10, only the two neighboring networks show up, the home network does not.  It is listed in preferences/network connections, of course, but somehow, someway, it is filtered out by Ubuntu 9.10.
Immediately after seeing how 9.10 filters away my home network, I can multiboot back to Vista and automatically connect to it.

HOW CAN THIS HAPPEN?

---

### Post by jheaton5 on 2009-11-07
Are you using Network Manager?  do you have network-manager-gui installed?  I am assuming we are talking about a wireless connection.

---

### Post by conrados1 on 2009-11-07
Do you have a Broadcom driver if so I have the files and directions to get you wireless connection working because I had the same problem.

---

### Post by jheaton5 on 2009-11-07
> **conrados1 said:**
> Do you have a Broadcom driver if so I have the files and directions to get you wireless connection working because I had the same problem.
The Broadcom drvers are available from System>Administration>Hardware Drivers.

---

### Post by stanley45 on 2009-11-08
Thanks for the replies.
No, I don't have a Broadcom adapter, a Linksys.

I don't have Network Manager installed that I know of.  Ubuntu 9.4 connected flawlessly with the configuration I preserved onto 9.10 .

But this mystery still happened.

---

### Post by michaelaudet on 2010-01-22
ubuntu is new to me too but not linux based systems, i have a broadcom wireless card and my internet works fine in windows seven but not in ubuntu. how do i go about getting this to work?

---

### Post by oscarcool40 on 2010-01-23
sorry to be bothering you guys but my computer thats ubuntu keeps saying

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

and so i do it and it keeps saying

Reading package lists... Error!
E: Unable to write mmap - msync (28 No space left on device)
E: The package lists or status file could not be parsed or opened.

and so now i dont have any options left but to turn to the glorious linux fans like i

---

