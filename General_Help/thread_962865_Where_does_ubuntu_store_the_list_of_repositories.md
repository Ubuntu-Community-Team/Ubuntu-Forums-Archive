---
title: "Where does ubuntu store the list of repositories"
date: 2008-10-29
forum: General Help
---

### Post by lykwydchykyn on 2008-10-29
No, I don't mean /etc/apt/sources.list

In synaptic, under repositories, you can select a repository server to use.  Does anyone know where this list is stored?  I'd like to edit it to see if I can get synaptic to recognize my local mirror.

I've grepped the whole filesystem, but I haven't turned anything up yet.  /var/lib/apt/mirrors is empty, but this data has to be somewhere.

---

### Post by spiderbatdad on 2008-10-29
System>>Administration>>Software Sources

---

### Post by geirha on 2008-10-29
/usr/share/python-apt/templates/Ubuntu.mirrors

---

### Post by jimbo99 on 2008-10-29
Look in the folder /etc/apt

You should find the sources file there, or under a folder in that folder.

---

### Post by lykwydchykyn on 2008-10-30
You rock geirha!  I would never have thought to look in /usr.  Wonder why my grep of / didn't turn that up.  I let it run all night.  Oh well.

Thanks all, looks like this is working.

---

