---
title: "Boots after Windows"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by andaanma on 2009-07-01
Hello, I have a ThinkPad w500 and I recently installed ubuntu 8.10 x86 version along side an exsisting windows xp installation. It only boots sometimes, and from what I've noticed, Ubuntu will properly boot only if i had shutdown in windows. When shutting down in Ubuntu it would stall at the last second of the shutdown and require a hard shutdown. 

When booting back up from that hard shutdown Ubuntu would load until it gave me something like:

kinit: no resume image
kinit: resume normal boot 

dropping to a command line login and never reaching gnome. I attempted fixing this by doing a mkswap and putting that uuid into /etc/fstab and .../config.d/resume. This allowed for a proper shutdown, but to no avail on the resume error.

Lastly, I also noticed that when booting up, the bios output was more clear (pixilated and less fuzzy) after i shutdown in windows and less clear (more fuzzy) when booting from the hard shutdown in Ubuntu. 

Any thoughts?

---

