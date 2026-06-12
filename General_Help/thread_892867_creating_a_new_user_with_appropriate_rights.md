---
title: "creating a new user with appropriate rights"
date: 2008-08-17
forum: General Help
---

### Post by andrewbadera on 2008-08-17
hello-

I'm running Hardy Heron on a P4 2.8Ghz HT with 2 gig of RAM and a decent HDD, but nothing super fast. It's mostly a development/test box for me, as well as hosting OpenSSH for remote connectivity and tunneling when I'm outside my home office.

I'd like to allow a friend to utilize the machine to get familiar with modern Linux, it's been a few years since he's worked off a command line. However, I don't want to expose 100% of everything, nor preferably put my Drupal, Reddit (Pylons), MySQL or PostgreSQL stuff at risk.

I'm no Linux guru ... I'm hoping someone could provide advice on the appropriate way of setting up a user to share the box, with enough rights to be able to explore and learn, to use SSH to access and tunnel, without giving away the keys to the house.

Also ideally, I'd rather not have my SSH tunnels choked, my residential cable connection is slow enough outgoing as it is -- I only get something like 880kbp/s when I'm tunneling from a remote location.

tia.

---

### Post by HalPomeranz on 2008-08-18
I'd just create a user account for your friend and make sure that they're NOT in the "admin" group.  That will mean they're allowed to log into the system (and set up tunnels if they want), but not allowed to use sudo to do commands as root.  Seems safe enough to me.

As for traffic-shaping based on the user ID, that's much harder.  Frankly, I wouldn't bother with it until it becomes a problem for you.

---

