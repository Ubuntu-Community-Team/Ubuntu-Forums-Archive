---
title: "Boot Option help need....PLease"
date: 2005-09-16
forum: Hardware &amp; Laptops
---

### Post by stevewabc on 2005-09-16
Im looking to set up grub with a (no network configure option) on my laptop to stop this hanging thats going on... 60% on the time im not on any network..

my grub configure at boot looks like this...

UUbuntu
Winshit XP


I want this:

Ubuntu
Ubuntu no network
Winshit XP

What do I do and how do I configure this option?

---

### Post by skoal on 2005-09-16
I can't say I recognize that particular Windows version you got there, but have you tried just creating a custom runlevel (using BUM, or manually) not to start the network?  Then, you just start it when you need it (the other 40% of the time). 

I do not know of a grub boot option which will do what you ask, since the init scripts off your root partition will get run regardless of what kernel option you pass (or even if you disable all network functionality in a custom kernel).

\\//_

---

### Post by stevewabc on 2005-09-16
ok im starting to understand this more so what im thing to do is as follows:


Default boot loads running level 5 correct?


I want to set up a 2nd boot option called (Ubuntu No network) witch will be running level 4 I hope this clears that up a little, I do under stand the Grub editing now.. but what I dont understand is the other part needing to be edited and configured.. In Fedora to set this up I would edit my running levels in system-config-services (Service Configuration) and turn off the network stuff 


I hope this help you all understand what im trying to due now....

---

### Post by stevewabc on 2005-09-17
I got it now thanks

---

