---
title: "View all applications loaded"
date: 2008-11-07
forum: General Help
---

### Post by b-boy on 2008-11-07
H i guys how can I view all applications loaded excluding the standard applications loaded with Ubuntu 8.04?

---

### Post by anystupidname on 2008-11-07
There are surely better ways to do this but you could:
1) perform your default install
2) aptitude install apt-show-versions
3) export the list apt-show-versions > list.txt
4) install weirdness
5) export the list again apt-show-versions > weirdness.txt
6) do a compare of list.txt and weirdness.txt

Also possibly useful
debfoster
tasksel --task-packages kubuntu-desktop (to list contents of a meta package)

---

### Post by b-boy on 2008-11-07
> **anystupidname said:**
> There are surely better ways to do this but you could:
1) perform your default install
2) aptitude install apt-show-versions
3) export the list apt-show-versions > list.txt
4) install weirdness
5) export the list again apt-show-versions > weirdness.txt
6) do a compare of list.txt and weirdness.txt

Also possibly useful
debfoster
tasksel --task-packages kubuntu-desktop (to list contents of a meta package)

thanks 

i will try that

---

