---
title: "User settings -&gt; manage groups broken in 9.04?"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by brianpatrick on 2009-04-18
Hi,
I am trying to get a root terminal to open and it is not working. I thought it might be something to do with my groups. I see myself in user settings and when I go to "manage groups" everything is grayed out except for the close button. 

I can see that I am in the admin group, but not in the root group and am wondering whether that could be the cause of the problem. 

I added myself to the root group with:
sudo adduser brianp root
but I still can not get a root terminal. 

What am I missing?

Thank you,
    BrianP

---

### Post by prshah on 2009-04-18
> **brianpatrick said:**
> 
but I still can not get a root terminal. 


From a regular terminal,
```
sudo -i
``` will give you a terminal with super-user powers.

(Request to admins: If this counts as a violation of the forums "non-root-login" policy, please remove; I apologize in advance).

---

### Post by brianpatrick on 2009-04-19
prshah,
As an old school Unix hacker, not having a root shell is like having to raise your hand to ask the teacher to go to the bathroom. 

I typed my password at least 100 times yesterday. Leaving the root shell in the menus and removing the feature is fraudulent advertising. 

Sudo is for weenies whom you don't trust with the root password. 

Thanks 1E6,
    BrianP

---

