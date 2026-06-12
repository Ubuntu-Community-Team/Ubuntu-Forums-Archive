---
title: "AsusFan - installing modules"
date: 2005-11-08
forum: General Help
---

### Post by serzz on 2005-11-08
I'm trying to get asufan working without nvclock installed. Found solution in Gentoo forums. Can anyone help me migrate this instruction to Ubuntu?

```

1. You would be needing only the asusfan binary (build it from CVS)
2. Open /etc/modules.d/nvidia in your favourite editor and add this line to it:
install nvidia /usr/local/bin/asusfan -m 1 --temp=75:70:65:60 ; modprobe --ignore-install nvidia
(notice that I have asusfan installed in /usr/local, please change accordingly)
3. Run "modules-update" and restart your system 

```

---

