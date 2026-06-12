---
title: "clean install but keep exist users, passwords"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by goneskiing on 2009-10-16
we always like to do clean installs, and keep all our data in a separate /home partiton so it's not touched.

but how can we keep or input existing users and their passwords to point to their existing /home/user folders.

creating a new user does not seem to allow putting in the existing user name.  this has always been a big hassle - thks for any feedback.

---

### Post by phillw on 2009-10-16
if you chop off the bits of the users from /etc/passwd   and /etc/shadow  You will be able to pop them back on your new system. This will even keep their UIDs the same, if you have set up user groups you're going to need the alterations made to /etc/group

I pretty sure that's all the files you need - But, I've never done it.

***ONLY DO THIS FOR YOUR GENERATED USERS - NOT SYSTEMS USERS LIKE mail, cron  etc !!***

Regards,

Phill.

---

