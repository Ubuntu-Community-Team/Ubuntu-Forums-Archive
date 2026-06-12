---
title: "Intrepid wont install updates"
date: 2009-01-26
forum: Hardware
---

### Post by silverbullet007 on 2009-01-26
hardy install on a T43 upgraded to Intrepid.  Ever since then Update Manager shows updates but when I click on Install Updates, enter my password..nothing.  No errors or anything.  Not sure where to look to resolve this one.

---

### Post by taurus on 2009-01-26
Make sure you close down the update manager first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by silverbullet007 on 2009-01-26
Ok that seems to be working.. it's pulling the updates down and installing them.  Ok so my issue is with update-manager itself then?

---

