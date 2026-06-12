---
title: "can use sudo but not su"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by tbobker on 2009-03-01
I have a xubuntu 8.04 intall. 

When i try and type commands that need su rights i cannot promote myself to super user because it says authentication fails however if i simply just use sudo in front of my command instead and type the same password it works?

Is this a problem and does anyone know why this is happening?

---

### Post by lloyd_b on 2009-03-01
> **tbobker said:**
> I have a xubuntu 8.04 intall. 

When i try and type commands that need su rights i cannot promote myself to super user because it says authentication fails however if i simply just use sudo in front of my command instead and type the same password it works?

Is this a problem and does anyone know why this is happening?
This is *normal*.  *buntu (Ubuntu, Xubuntu, Kubuntu) do not have a "root" user (at least, not one you can log into), so it's impossible to "su" to root.  Instead, it uses the "sudo" mechanism to provide access to superuser commands.

If you *really* want a root shell, "sudo su" does the trick...

Lloyd B.

---

