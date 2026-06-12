---
title: "[Newbie] Command to add at boot"
date: 2005-12-15
forum: Installation &amp; Upgrades
---

### Post by NothingHere on 2005-12-15
Hello all,

Sorry for my stupid question, I've read some of how-to about init.d, update-rc.d and other, but I can't find anything.
I've just seen a lot of doc about "chkconfig".

I juste want to do automaticly type 2 line at boot :
dhclient eth0
/opt/apache/bin/apachectl start

Can I add these two line in a bash script (with chmod +x) wich is executed each boot ?

How can I do that ?

Thanks ...

(I'm not using X, I'm in runlevel 3, console mode, ubuntu 5.10 installed in server mode)

---

### Post by Zelut on 2005-12-15
Well it sounds like , you're right, it should be in the init.d/ scripts area.  the dhclient eth0 looks like something that should/would be in your /etc/network/interfaces file (take a look, that auto-loads at boot too).

As far as the other, I'm not familiar with the command so I'm not sure where else it'd be.  I'm assuming you have /etc/init.d/apache2 (may or may not be completely different).  Take a look at one of the scripts in /etc/init.d/ and see how they are put together.  Try to make your own off of those templates..

---

### Post by NothingHere on 2005-12-16
Thanks !

I have added, in /etc/network/interfaces this line :
auto eth0

Thanks for your help, I'll continue to search for apache ...

---

