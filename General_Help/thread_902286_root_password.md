---
title: "root password"
date: 2008-08-27
forum: General Help
---

### Post by Low_E on 2008-08-27
is there a way to change the root-password (as being a user with admin-rights?)

---

### Post by coffeecat on 2008-08-27
For reasons why you may not get this answered, see:

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

and

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sameerds on 2008-08-27
> **coffeecat said:**
> For reasons why you may not get this answered, see:

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

and

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The original poster has actually cross-posted this query, and with insufficient information. Elsewhere, the other posts mentions that the root password is already set, and it doesn't work anymore. I wonder if there is an official howto for getting *out* of this situation!

---

### Post by Low_E on 2008-08-27
OK thx for the help.

The reason I was not able to get some results while using sudo, was that I had to restart my system.
Certain functions were locked and so I really thought I needed the root-account.

THX, I learned again :)

---

### Post by coffeecat on 2008-08-27
> **sameerds said:**
> Elsewhere, the other posts mentions that the root password is already set, and it doesn't work anymore. I wonder if there is an official howto for getting *out* of this situation!

No, there isn't - the first link I posted tells you why. You don't need a usable root password - the second link I posted tells you why.

Yes, I do know how to change/activate the root password. No, I'm not going to tell you how. :p The first link tells you why not.

And I never activate the root password for myself. The second link explains why. :lol:

---

### Post by Low_E on 2008-08-27
2e that.

---

### Post by sameerds on 2008-08-27
> **coffeecat said:**
> No, there isn't - the first link I posted tells you why. You don't need a usable root password - the second link I posted tells you why.

Yes, I do know how to change/activate the root password. No, I'm not going to tell you how. :p The first link tells you why not.

And I never activate the root password for myself. The second link explains why. :lol:

I appreciate your zeal at keeping me [sic] from shooting myself in the foot. But what I was asking about is the opposite ... if a user has already been misled and ends up in the situation where the root password has been set, is there a howto to help that user get out of the situation.

---

### Post by sisco311 on 2008-08-27
> **sameerds said:**
> I appreciate your zeal at keeping me [sic] from shooting myself in the foot. But what I was asking about is the opposite ... if a user has already been misled and ends up in the situation where the root password has been set, is there a howto to help that user get out of the situation.
you can re-disable the root account with:
```
sudo passwd -l root
```

---

