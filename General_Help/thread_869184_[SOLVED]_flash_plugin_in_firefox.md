---
title: "[SOLVED] flash plugin in firefox"
date: 2008-07-24
forum: General Help
---

### Post by pikabuntu on 2008-07-24
I have gnash, but it does not work.  I have tried to install the nonfree flash player, but i don't think that i did it right.  

Flash videos are black for a couple seconds, then they turn white and stay like that.  There is no sound.

---

### Post by tarasin on 2008-07-24
did you uninstall gnash?

---

### Post by pikabuntu on 2008-07-24
How can I do that?

---

### Post by tarasin on 2008-07-24
go to add remove programs or synaptic package manager search for gnash and remove it.
also how did you install flash non free plugin?

---

### Post by nwubie on 2008-07-24
If you installed the gnash plugin from within Firefox then it installed the following packages : 

libboost-date-time1.34.1
libboost-thread1.34.1
gnash-common
gnash
mozilla-plugin-gnash

Type
**sudo apt-get remove libboost-date-time1.34.1**
and all dependencies should be uninstalled (the first installed package is usually the one the other packages depend from).

---

### Post by pikabuntu on 2008-07-24
sudo apt-get install flashplayer-nonfree

---

### Post by pikabuntu on 2008-07-24
what would be the best way to install it?

---

### Post by pikabuntu on 2008-07-24
gnash is uninstalled now

---

### Post by pikabuntu on 2008-07-24
um nevermind....
after i ran 
[B]sudo apt-get remove libboost-date-time1.34.1
[/B]it works now :)

---

### Post by nwubie on 2008-07-24
good news :D

---

### Post by crypope on 2008-07-26
I had a similar issue and doing all the above didn't fixed my flash plugin in Firefox till I went to:

Tools -> Add-ons -> Plugins -> "Shockwave Flash" and Enabled it. Somehow no matter what I was doing to install it is was default set to Disable.

After I enabled I had Shockwawe Flash 9 working with sound and images.

---

