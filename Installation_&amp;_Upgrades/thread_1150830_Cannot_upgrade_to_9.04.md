---
title: "Cannot upgrade to 9.04"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by sdd231163 on 2009-05-06
On running update manager on 8.10 I select 'upgrade'.

This gives me the release notes and I select 'upgrade' again.

Two files are downloaded for the upgrade tool.

I then get the following message: "Authentication failed - Authenticating the upgrade failed. There may be a problem with the network or with the server." 

What do I need to do to upgrade?

Thanks,
Stephen.

---

### Post by kshane on 2009-05-06
> **sdd231163 said:**
> On running update manager on 8.10 I select 'upgrade'.

This gives me the release notes and I select 'upgrade' again.

Two files are downloaded for the upgrade tool.

I then get the following message: "Authentication failed - Authenticating the upgrade failed. There may be a problem with the network or with the server." 

What do I need to do to upgrade?

Thanks,
Stephen.

Try changing your software sources.  That would be my first thing to try.

---

### Post by sdd231163 on 2009-05-06
Tried changing the sources but to no avail.

---

### Post by matthewboh on 2009-05-06
I'm having a similar problem - I get the two files downloaded and then closes with no error message.  One of the things that I've noticed is that if I go to System | About Ubuntu | Version and Release Numbers - they're not there.  I've attached a screen shot.  I'm currently running 8.10 on a dual boot machine with XP

---

### Post by sdd231163 on 2009-05-07
I solved this:

I started update manager from a terminal using sudo:

sudo update-manager

Everything worked well from there.

---

### Post by matthewboh on 2009-05-11
I did this and it worked, but now Firefox doesn't work.  It says that it can't reach the Internet, but I can ping anything out there

---

### Post by sdd231163 on 2009-05-11
I don't know, but try uninstalling (purging) and reinstalling it?

---

### Post by matthewboh on 2009-05-12
Did that, but doesn't work.  I find that I can hit some web sites but not others - on the exact same network, Ihave two other PC's and I don't have any problems - they both look like they're set up the same.  I'm going to follow the forums about issues with firefox connecting

---

