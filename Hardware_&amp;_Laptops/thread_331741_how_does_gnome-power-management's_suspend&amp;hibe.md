---
title: "how does gnome-power-management's suspend&amp;hibernate work?"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by matva on 2007-01-05
hi,

gnome-power-managment suspend doesn't work for me:(

i get a funny red,blue,green,white screen loop on resume.

if i edit the /etc/hibernate/hibernate.conf to:
UseACPISleep 3
LoadModules auto
SwitchToTextMode yes
UseDummyXServer yes

suspend works fine.

id like to change things so that gnome will execute the "hibernate" command when suspension is necessary (e.g. when i press the suspend button in logout options or when i say "suspend after 15mins of inactivity").

i cant make much of the previous hibernate script. so where are gnome-power-managements scripts suspend/hibernate scripts held if i cant change it to reference hibernate.conf i can just edit the scripts it does reference .. no?
hehe in the end suspend is still far inferior to windows equivelent

---

