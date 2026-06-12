---
title: "Hoary hangs on Testing Network Repository"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by elgrego on 2005-04-15
Just saw that this is in the wrong forum. sorry

Hi,

Im installing Ubuntu on VMWare 5.0 on my xp workstation at work.
Everything is fine until reaching "Configuring apt" - > "Testing network Repository"
I have done the same installation at home with the only differense network wice is that we use a proxy-server at work.
Can this affect the installation when testing the network repository?
I have tried waiting for a timeout, but it did not happen during the night so now Im fresh out of ideas.

Any help appreciated.


Regards // Greger

---

### Post by lao_V on 2005-04-15
Before booting up your guest OS, change your network type to NAT instead of Bridgened and it should work fine!

---

### Post by windymiller on 2005-04-15
I had this problem because I misconfigured my wireless settings during the install process.  If you leave it for long enough (about 5-10 minutes) it'll eventually give up and carry on with the install.

The timeout should definitely be smaller though.

---

