---
title: "Smartmon deactivates network manager and network interface"
date: 2010-05-07
forum: Hardware
---

### Post by bilodeau on 2010-05-07
Howdy All,

I thought I'd share my solution to a strange problem I had with Ubuntu 10.04.

I installed the SMARTMon package to keep track of my hard drives.  After the software install, my screen jumped to the text mode for a few seconds and then back to my regular Gnome session.  I noticed that my network-manager indicator said that my network was down.

I did a bit of investigating, and yes, my network was down.  To get it back up and running, I did:

~$ sudo start networking

Now I could use Firefox to see websites.

However, the network manager applet said that the network connection was down.  To get it back in a consistent state with the network, I did:

$ sudo start network-manager
network-manager start/running, process 30378

So, it appears that I didn't actually do anything, but now my network manager applet is in a state that corresponds with reality - my network interface is active, running, and communicating with the outside world.

---

