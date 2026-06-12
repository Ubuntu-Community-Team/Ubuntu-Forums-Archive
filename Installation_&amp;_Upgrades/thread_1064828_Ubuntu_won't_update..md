---
title: "Ubuntu won't update."
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by KanineN on 2009-02-09
Hello,

when I was trying to update my Ubuntu 8.10 I got a error message

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I tried that command at the terminal but it didn't work,

```
sudo: dpkq: command not found
```

Help please.

---

### Post by snowpine on 2009-02-09
> **KanineN said:**
> Hello,

when I was trying to update my Ubuntu 8.10 I got a error message

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I tried that command at the terminal but it didn't work,

```
sudo: dpkq: command not found
```

Help please.

You spelled 'dpkg' wrong (it's a g, not a q).

---

### Post by KanineN on 2009-02-09
Oh, thanks.

But now I get this problem

```
Setting up perl-modules (5.10.0-11.1ubuntu2.2) ...
dpkg: error processing libc6-dev (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 libc6-dev

```

How can I install that lib when I can't install anything?

---

