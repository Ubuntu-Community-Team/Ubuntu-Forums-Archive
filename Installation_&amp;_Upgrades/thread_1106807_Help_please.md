---
title: "Help please"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by katnalie on 2009-03-26
My computer restarted while was installing the updates and now the sound doesnt works and i get same error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report." .I followed your instruction...and in terminal i get this user@grup:~$ sudo dpkg --configure -a && sudo apt-get -f install
[sudo] password for user:
Setting up linux-image-2.6.24-24-generic (2.6.24-24.51) ...
Running depmod.

and is stucked....
 What could i do ?

---

### Post by katnalie on 2009-03-26
I tried also  sudo apt-get update and it says 
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
katny@theone:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by sahabcse on 2009-03-26
Hi

Try to login to the command mode. alt+ctrl+f1 type username and password. Then run #sudo startx

---

### Post by katnalie on 2009-03-26
I did and i get this message: Fatal server error
 Server is already active for display O If this server is no longer runing remove /tmp/.XO - lock and start again.Well i am pretty new on linux,Ubuntu so could soemone help me please ?

---

### Post by sahabcse on 2009-03-26
Hi

Just restart the server and update

---

### Post by sahabcse on 2009-03-26
Hi

Follow the url [http://ubuntuforums.org/archive/index.php/t-339266.html](http://ubuntuforums.org/archive/index.php/t-339266.html) - similar issue

---

