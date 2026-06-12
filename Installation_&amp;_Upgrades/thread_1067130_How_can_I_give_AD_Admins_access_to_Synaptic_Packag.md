---
title: "How can I give AD Admins access to Synaptic Package Manager"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by jtliii on 2009-02-11
I am trying to configure Ubuntu 8.04 to allow Active Directory domain admins access to the Synaptic Package Manager.

It was pretty easy to add the machine to the domain and I have added domain admins to sudoers:

sudo visudo
%domain_name\\domain^admins ALL=(ALL) ALL

Now I want to give them access to the Synaptic Package Manager but when I try to add it to the menu the box automatically unchecks itself.  I can get local users access but I need to be able to give domain admins access.

Any help would be greatly appreciated.

---

