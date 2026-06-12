---
title: "Suspend/resume broken in 8.04 on Dell Inspiron 9400 ?"
date: 2008-04-28
forum: Hardware
---

### Post by Glenn Coombs on 2008-04-28
I did a clean install of 8.04 onto a Dell Inspiron 9400 and suspend/resume doesn't work properly.  The first suspend (Fn+Escape) after a cold boot works fine and the system suspends in 2 or 3 seconds.  When I wake it up though it makes a high pitched whining noise when idle.

And then any subsequent attempts to suspend fail.  They look like they are going to work but after the screen turns off nothing happens for a few seconds and then the screen comes back to life and I am at the lockscreen prompt.

Has anybody else experienced this problem and found a solution to it ?

I should point out that suspend/resume works fine on this system under Ubuntu-6.10 and that I have already eliminated wifi and graphics driver problems by rmmod'ing fglrx,iwl3945 and iwlwifi_80211.

--
Glenn

---

### Post by damian.obrien on 2008-05-01
Same problem.  Same setup.  Any luck?

---

### Post by schmolch on 2008-05-03
Same problem on a Thinkpad X60T.

---

### Post by Glenn Coombs on 2008-05-05
No, I haven't found a fix for this problem so far.  Have a look at the following bug report:

    [https://bugs.launchpad.net/bugs/220607](https://bugs.launchpad.net/bugs/220607)

as I think that one is an exact match for the problem.  Add your details to that report so that the developers have as much information as possible.

---

### Post by lazyron on 2008-05-27
I'm having the same problem with an e1405 Dell Inspiron. Unfortunately, I don't have much to add, except I found another bug being tracked that seems to describe this bug a little better and offers some work around, but no fixes.

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521)

---

