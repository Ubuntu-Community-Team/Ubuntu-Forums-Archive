---
title: "How to copy user information across distributions?"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by dawynn on 2009-08-14
I have maintained my own multi-boot machine for many years.  As long as I only had one user, everything always worked fine.  I could install multiple distributions, and I would always have the same home directory, which all the various logins could share.

Now I'm trying to establish a computer for the whole family that will also have two different grub distributions (probably the stable version, and the test version).  I've got "distributions" on right now, although both are at various incarnations of 9.04 Ubuntu.

Here's the dilemma.  As I was installing on each of these systems, I set up myself as the first user.  All well and good.  I'm up and running on both systems -- and I can use my home directory just fine.  On the first system I installed, I have three other established users.  I tried to build one of these users into the new system, and for whatever reason, it doesn't want to share the home directory, even though I tried to create the user the same way on both systems.  The new system is choking and telling me that the user is already established.  I tried renaming the old home directory and letting the system create a new one.  That works fine, on the new system -- but now the old system doesn't recognize the home directory as belonging to that user.

So, how can I safely copy all user information from the first distribution over to the new distribution so that, whichever distribution anyone logs into, they can use the same /home directory?

---

### Post by dawynn on 2009-08-16
* bump *

Is this really something new?  I have four users on my established partition.  Now I've created a new partition, and just want to use the same user settings, same passwords, same /home directory.  How do I copy the user information so the new partition recognizes all the users?  (Yes, the /home directory is already a shared partition between the two systems)

---

### Post by slakkie on 2009-08-16
> **dawynn said:**
> * bump *

Is this really something new?  I have four users on my established partition.  Now I've created a new partition, and just want to use the same user settings, same passwords, same /home directory.  How do I copy the user information so the new partition recognizes all the users?  (Yes, the /home directory is already a shared partition between the two systems)

You need to make sure that the UID is the same.. 

System A:

useradd -u 1003 ...

System B:

useradd -u 1003 ... 

Also giving them the same group id's is an idea, for more info man useradd

---

### Post by dawynn on 2009-08-17
That did the trick.  Thank you very much!

---

