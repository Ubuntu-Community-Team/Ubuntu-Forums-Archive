---
title: "Sudo error: sudo: /etc/sudoers is mode 0777, should be 0440"
date: 2008-09-25
forum: General Help
---

### Post by PostersandGuitar on 2008-09-25
sudo: /etc/sudoers is mode 0777, should be 0440


I get this when attempting to sudo. How do I fix it?

---

### Post by Nepherte on 2008-09-25
You have to edit that file with the visudo command. Just because otherwise the permissions get messed up. I even think that advice it's in the file itself. So:
```
sudo visudo
```

---

