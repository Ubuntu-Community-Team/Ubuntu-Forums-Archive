---
title: "januty installs python packages in 2.5 but 2.6 is default"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by localetc on 2009-06-26
apt-get has installed all my python packages in 

/usr/lib/python2.5/site-packages/

but then we have:

lrwxrwxrwx 1 root root       9 Jun 26 08:33 /usr/bin/python -> python2.6

and mod_python is pointing to 2.6.  There isn't even a site-packages folder for 2.6.  I must be missing something right?  Python couldn't be this messed up in Jaunty?

I am working on a brand new system76 machine and I have only been using apt-get

---

### Post by cmwslw on 2009-06-26
> **localetc said:**
> apt-get has installed all my python packages in 

/usr/lib/python2.5/site-packages/

but then we have:

lrwxrwxrwx 1 root root       9 Jun 26 08:33 /usr/bin/python -> python2.6

and mod_python is pointing to 2.6.  There isn't even a site-packages folder for 2.6.  I must be missing something right?  Python couldn't be this messed up in Jaunty?

I am working on a brand new system76 machine and I have only been using apt-get

Did you try purging python using apt-get purge python and reinstalling using apt-get install python. That might mess with some dependencies but make sure you keep track of all the packages uninstalled so you can reinstall. I'm using jaunty and python was installed fine for me.

---

### Post by localetc on 2009-06-26
It looks like it is just a problem with clearsilver:

[https://bugs.launchpad.net/ubuntu/+source/clearsilver/+bug/386970](https://bugs.launchpad.net/ubuntu/+source/clearsilver/+bug/386970)

Everything else is fine (the packages are in /usr/share/pyshare)

---

