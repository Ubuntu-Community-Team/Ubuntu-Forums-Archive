---
title: "Both Add/Remove &amp; Update Manager is messed up!"
date: 2008-08-05
forum: General Help
---

### Post by nelsonm on 2008-08-05
I'm running Ubuntu 8.04 with all but the latest updates. All of a sudden...

The program that controls these interfaces is messed up. They will start up and populate but i can't install or update anything. They just sit there and spin their wheels.

I can't even X out of them.

Whats up?

---

### Post by loell on 2008-08-05
you can try the command line interface

```
sudo apt-get update
```

and 

```
sudo apt-get install -f
```

any errors, just paste it here :)

---

### Post by nelsonm on 2008-08-05
I just figured it out!

A few days ago I changed the host alias in Network Settings for 127.0.1.1 from LINUX-FAMILY (the original computer host name) to LINUX-3.

I changed it back and now both Add/Remove & Update Manager work fine.

Somehow, it messed up both Add/Remove & Update Manager. They probably could not resolve the host name.

I guess if I change the host name I need to change it in more than one place like the host file.

What do you think?

---

### Post by loell on 2008-08-05
if you change the **hostname** you can change it, but its a bit strange that it will affect how your apt in querying and updating *from* the repository :-k

---

### Post by nelsonm on 2008-08-05
The issue is that if you want to change the host name/alias, you must change it in both the hosts & hostname files.

I only changed the alias in the hosts file through the network settings host properties.

Appearently, it does mess up the Add/Remove & Update Manager.

---

