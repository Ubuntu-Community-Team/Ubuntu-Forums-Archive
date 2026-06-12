---
title: "How to add a kernel module from beginning of the boot process"
date: 2008-08-23
forum: General Help
---

### Post by psie on 2008-08-23
Hey, I want to add the module dm-crypt from the beining of the boot process even before LUKS (I have my file system encrypted) askes for my password. How can I do this? Is there a way to compile my actual kernel with this module as well?

Thanks

---

### Post by maniheer on 2008-08-23
I don't know about ubuntu but on Arch

```

sudo gedit /etc/rc.conf

```

and at the bottom of the file is the title Daemons, mine looks like this

```

#-----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng @network netfs crond hal fam kdm)

```

Hope this helps

---

### Post by carolinason on 2008-08-23
From the fabulous manual

[http://kernel-handbook.alioth.debian.org/ch-modules.html](http://kernel-handbook.alioth.debian.org/ch-modules.html)

---

