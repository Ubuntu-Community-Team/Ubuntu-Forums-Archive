---
title: "Correct Root Password Ignored"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by efparri on 2005-12-27
I setup Ubuntu Breezy Badger to test on a Compaq Armada 3500.  After Gnome loaded I got the notice that I had Upgrades.  I clicked on the icon and entered my Root password at the prompt.  A window told me that the paswword was incorrect.  Thinking that I might have typed the password incorrectly during installation, I tested the password in a terminal window.  It worked correctly.  Each time I try that password with Update Manager or Synaptic Package Manager, I get the incorrect password error.  I had no similar issue with Debian or other Linux distributions I have tested.

---

### Post by kaamos on 2005-12-27
Just about everything in ubuntu uses sudo so the apps are asking for your **user** password.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by efparri on 2005-12-27
Thank you.  I thought about that but did not try it because it was late at night.

---

