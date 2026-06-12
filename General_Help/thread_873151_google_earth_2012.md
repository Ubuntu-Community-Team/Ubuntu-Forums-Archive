---
title: "google earth 2012"
date: 2008-07-28
forum: General Help
---

### Post by SpenceMakesSense on 2008-07-28
When I start google earth the planet never shows up. I got 4.3.7284.3916 (beta). So two things might help me. How do I uninstall this to install a non beta. Or does someone know what the problem is. :confused:

---

### Post by jonian_g on 2008-07-28
How you installed google earth? From the medibuntu repositories or with a .bin installer?

---

### Post by SpenceMakesSense on 2008-07-28
the .bin installer from the site

---

### Post by SpenceMakesSense on 2008-07-29
bump

---

### Post by jonian_g on 2008-07-30
Sorry I forgot this post!

If you installed google earth with sudo and haven't changed the default install path, open a terminal and type:

```
cd /opt/google-earth
```
 and
```
sudo ./uninstall
```

If you installed without sudo, navigate to the folder that google earth is installed (/home/username/google-earth if you haven't changed the default install path) and doubleclick the uninstall executable.
From the terminal:

```
cd google-earth
```
 and
```
./uninstall
```

Then go here:

[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

and download version 4.2 of google earth and install it (it's in the bottom of the page).

---

