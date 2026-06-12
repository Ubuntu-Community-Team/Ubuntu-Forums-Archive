---
title: "Login problem after upgrade 5.04 -&gt; 5.10"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by taidur on 2005-12-18
After upgrade I recive that kind of error message before the login

*************
Configuration is not correct

The configuration file contains an invalid command line for the login dialog, so
running te default command. Please fix your configuration.

**************

When I answer "Okay" I can log in.

Can anybody tell me which configuration file should I fix and what is the possible problem? That error message in not very informative for me.

---

### Post by mlomker on 2005-12-18
If you run gnome then I'd try reinstalling the **gdm** package.

---

### Post by taidur on 2005-12-18
-

---

### Post by taidur on 2005-12-18
Yes I use Gnome.
I reinstalled gdm package. It didn't help. Moreover, it seems that things have gone worse. For example, if I try to run System -> Administration -> Login Screen Setup I receve an error:

Failed to run gdmsetup as user root. Child terminated with 1 status

---

### Post by mlomker on 2005-12-19
I'd try doing a 'complete removal' in Synaptic and then install it again.  I'm assuming that one of the configuration files is damaged.

---

