---
title: "Autofs will not start properly"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by kerdawg on 2009-04-09
Greetings,  I'm back on Ubuntu after a stroll with several other distros and pleased to be back.  I am having one annoying issue.  I'm in a NIS environment and cannot seem to get the autofs to run during boot.  I can log in and manually run /etc/init.d/autofs restart then log out and back in as my NIS user and life is good.  But I can't get it to start on its' own.  I've tried several of the obvious fixes to no avail...any ideas?  Thanks...

---

### Post by mbay2002 on 2009-10-02
> **kerdawg said:**
> Greetings,  I'm back on Ubuntu after a stroll with several other distros and pleased to be back.  I am having one annoying issue.  I'm in a NIS environment and cannot seem to get the autofs to run during boot.  I can log in and manually run /etc/init.d/autofs restart then log out and back in as my NIS user and life is good.  But I can't get it to start on its' own.  I've tried several of the obvious fixes to no avail...any ideas?  Thanks...


I'm seeing the same thing on Jaunty... looks like this is a recently re-opened bug (#119660):
[https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/119660](https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/119660)

---

