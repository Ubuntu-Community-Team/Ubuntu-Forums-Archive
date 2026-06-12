---
title: "roxterm launched when I first log in"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by rrwo on 2009-02-01
When I first log in, some process is starting an instance of roxterm.  This has nothing to do with my preferred terminal application: no matter what I change it to, something is trying to run roxterm.  

Even if I uninstall roxterm, but create a dummy "roxterm" script in my path, something tries to run it.  There are no options passed to it, though. 

Of note: when roxterm is actually called by this process, the colour profiles and font profiles don't work, and can't be changed in that window.

I've tried disabling all of the autostarted apps, but this doesn't help.

Any idea what could be calling it? Or how I can write a bash script that can trace what is calling it?

This has happened since upgrading from Hardy to Intrepid.

---

### Post by rrwo on 2009-03-10
This seems to have just gone away, for reasons I odn't understand. It may have been that there was a session saved.

---

