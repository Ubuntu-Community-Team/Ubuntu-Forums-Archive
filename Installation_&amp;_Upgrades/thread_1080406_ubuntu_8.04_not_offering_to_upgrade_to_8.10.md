---
title: "ubuntu 8.04 not offering to upgrade to 8.10"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by xafwodahs on 2009-02-25
As per the instructions, I changed

  Software Sources -> Updates -> Show new distribution releases

to "Normal releases".

The "Ubuntu updates" section has 'important security' and 'recommended' boxes checked.

I also competed the update of all components for 8.04.

Now, when I run "Check" in Update Manager, I expect to be presented with a prompt to upgrade to 8.10, but instead it just says my system is up to date.

How can I get the system to realize there is an 8.10 version available?

---

### Post by cariboo on 2009-02-25
Press Alt-F2 and type:

```
gksu update-manager -d
```

This should allow you to update to Intrepid.

Jim

---

### Post by xafwodahs on 2009-02-28
> **cariboo907 said:**
> Press Alt-F2 and type:

```
gksu update-manager -d
```

This should allow you to update to Intrepid.

Jim

Ok, that worked.  Thanks.

Strange that the GUI method didn't work.

Also strange that after the upgrade, the "System->About Ubuntu" page doesn't list any version anymore.  It says:

> "Thank you for your interest in Ubuntu - the - released in ."

However, "lsb_release -a" confirms I am now on Intrepid.

Should I submit these as bugs?

---

### Post by darkstaar on 2009-02-28
> **xafwodahs said:**
> "Thank you for your interest in Ubuntu - the - released in ."

I'm running 9.04 A5 which has the same "bug" Also, on the "Version and Release Numbers" page, it states:
> This version () was released in  so its version number is .
...which leads me to believe that this document hasn't been looked at or updated in a while.

Not that it's a big thing but I wonder how many versions back this "bug" goes.

--Leisa

---

