---
title: "Update manager issue."
date: 2008-08-25
forum: General Help
---

### Post by randipoling on 2008-08-25
I have un-installed and re-installed Ubuntu multiple times, and this only happens on my laptop.  I go to update it, but as it goes to update the Update manager, It freezes the wholeee system.  No hard drive activity lights or anything.  I reboot by holding the power button since it is the only way.  The I log back on, and the sound driver is missing, and I go to update again, but I get this error...

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

also..whenever i go to type "su" in the console and enter my password, it say Authentication Failed"

Please help...

---

### Post by morbid_bean on 2008-08-25
> **randipoling said:**
> I have un-installed and re-installed Ubuntu multiple times, and this only happens on my laptop.  I go to update it, but as it goes to update the Update manager, It freezes the wholeee system.  No hard drive activity lights or anything.  I reboot by holding the power button since it is the only way.  The I log back on, and the sound driver is missing, and I go to update again, but I get this error...

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

also..whenever i go to type "su" in the console and enter my password, it say Authentication Failed"

Please help...


Open terminal and type   "sudo dpkg --configure -a" with out quotes and it should fix your update issue

---

### Post by sisco311 on 2008-08-25
In Ubuntu, by default, the root account is disabled.
Prepend *sudo *to the command you would run us root:
```
sudo dpkg --configure -a
```*sudo *will ask for your user password.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by randipoling on 2008-08-25
i just re-installed it...so my issue isnt...the first time this has happend?  I was liek..omg...what did i do >_< because i thought i did something worng, i will try the sudo command and seee if it gets me up and running again if ti happens.  I appreciate your guys help, Id be lost in the ubuntu world with out it.:)

---

### Post by randipoling on 2008-08-25
i just used the command in the terminal...its taking a while, but well see how it goes...

Update: It worked, Thanks for the help.

---

