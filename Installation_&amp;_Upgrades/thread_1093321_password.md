---
title: "password"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by BillyBoy0001 on 2009-03-11
I am running Ubuntu 8.10 with myself as admin and son as user. When I am on his user and try to use synaptic package manager it asks for a password. I type in my password which I use to get on the computer and it says it is incorrect. If i am the admin then why would I not be able to use the manager. Because I'm under another user maybe? Thanks

---

### Post by taurus on 2009-03-11
Because your son's account doesn't have root privilege.  Therefore, he is not allowed to start any program that requires root privilege.  So, you need to log back into your account and run synaptic again _unless_ you want to add him to group admin in /etc/group which is not a good idea because he could use sudo/gksudo and trash your machine.

---

### Post by Neo_The_User on 2009-03-11
> **taurus said:**
> Because your son's account doesn't have root privilege.  Therefore, he is not allowed to start any program that requires root privilege.  So, you need to log back into your account and run synaptic again _unless_ you want to add him to group admin in /etc/group which is not a good idea because he could use sudo/gksudo and trash your machine.

Yeah kids do that. When I was 10 I did that all the time.

---

