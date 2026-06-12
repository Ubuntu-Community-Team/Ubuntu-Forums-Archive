---
title: "kernal panic"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by Brigrat on 2005-12-30
I pulled the biggest of noob errors and did not check it 2x. I installed the wrong kernal package and now get a kernal panic lock up.  I was told to use "apt-get remove kernal (insert syntac "2.6.12-10-k7") and it comes back with a package not found.  I can use escape to stop the grub and select the last good kernal. So here are my questions.

A. can I go in through the last known good kernal and load the correct kernal this time?

b. Do I have to remove the bad kernal  Ie the amd kernal trying to run on intel hardware?:confused:

---

### Post by kaamos on 2005-12-30
Yes, you can just select the kernel you used to use. Once logged in you can then search in synaptic for the amd kernel you have installed, and remove it.

The system should boot just fine to your last good kernel.

---

### Post by Brigrat on 2005-12-30
Thanks I had a post also in the beginners section and got pointed in the right direction the system is right now happily installing automatix and doing fine!!!!!

---

