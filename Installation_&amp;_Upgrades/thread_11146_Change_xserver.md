---
title: "Change xserver"
date: 2005-01-14
forum: Installation &amp; Upgrades
---

### Post by chrislaurie on 2005-01-14
Hi All - from a complete newbie.

When Ubuntu booted from my har disk it asked me for the server to use for xserver. I misunderstood the instruction and entered VIA (what I though my chipset manufacturer was). This was wrong as the xserver failed to iunitialise.

Using Knoppix I see that I should have chosen vesa. How do I change this? (assume I bearly know how to log on to ubuntu command line).

Cheers

Chris Laurie

---

### Post by chrislaurie on 2005-01-14
Searching these froums I found a message that showed how I must edit the /etc/X11/XF86config file with nano.

One thing I did not know at the time was how to get root (and therefore write) access. Evantually found out about the sudo command.

Cheers

---

### Post by hashimoto on 2005-01-14
Well, you seem to be a quick learner! Good that you got it fixed and welcome to Ubuntu.

BR
Hashimoto

---

### Post by silgit on 2005-01-14
you can also use  

sudo dpkg-reconfigure xserver-xfree86

this ll let you set up X again

---

