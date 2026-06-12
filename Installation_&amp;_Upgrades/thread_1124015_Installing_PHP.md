---
title: "Installing PHP"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by SeanSee on 2009-04-12
I am trying to install PHP 5.2.9 and I assume it should be in the root directory but when I try to extract it I'm told I do not have root privileges.  I set the system up with only 1 user, myself, but I don't know how to grant myself root privileges with the extract program.  Do I need to put PHP in the root directory where apache and the other programs are?

---

### Post by lykwydchykyn on 2009-04-12
You can install php5 quite easily using synaptic or apt-get.  Have you tried:
```

sudo apt-get install php5

```

Are you just trying to set up a LAMP server?  You can also do 
```

sudo tasksel install lamp-server

```

---

### Post by SeanSee on 2009-04-12
Thanks.. the LAMP command worked perfectly.  and yes I'm trying to set up a web server but I just switched from windows to linux so I'm learning as I go.  Slowly but surely

---

