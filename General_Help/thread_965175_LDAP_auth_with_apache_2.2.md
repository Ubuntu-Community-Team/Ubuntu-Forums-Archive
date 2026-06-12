---
title: "LDAP auth with apache 2.2"
date: 2008-10-31
forum: General Help
---

### Post by rbblue8 on 2008-10-31
Hey all,

Been trying to get apache to be able to auth against my windows domain for some time now and i have been suck trying to get a module installed for Apache to use to auth against.

It comes down to the fact that i need the LDAP C SDK files so i can compile the module necessary from command line.

or..

is there a package that i can install from apt-get and just link the module into apache?

---

### Post by Titan8990 on 2008-10-31
I'm not 100% but I believe in order to do what you are trying to do you have to use Windbind to join your Linux box to the Windows domain.

---

