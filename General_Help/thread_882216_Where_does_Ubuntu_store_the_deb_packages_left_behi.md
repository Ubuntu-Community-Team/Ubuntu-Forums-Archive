---
title: "Where does Ubuntu store the deb packages left behind after install?"
date: 2008-08-06
forum: General Help
---

### Post by Comhra on 2008-08-06
I'm getting a little short of space and I want to delete them.  Should know this myself but I've forgotten.

---

### Post by perlluver on 2008-08-06
> **Comhra said:**
> I'm getting a little short of space and I want to delete them.  Should know this myself but I've forgotten.

sudo apt-get clean

Packages are located in /var/cache/apt/archives

---

### Post by Comhra on 2008-08-06
TY Pearl.

---

### Post by perlluver on 2008-08-06
> **Comhra said:**
> TY Pearl.

Yw, please mark as solved.

---

### Post by jonian_g on 2008-08-06
Or you can go to synaptic settings>preferences and on the Filres tab click "delete files from cache".
Also you can select "Delete downloaded packages from cache after installation" and you will not need to repeat the above.

---

