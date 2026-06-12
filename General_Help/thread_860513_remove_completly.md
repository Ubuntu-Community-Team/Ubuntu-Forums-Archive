---
title: "remove completly?"
date: 2008-07-15
forum: General Help
---

### Post by StOoZ on 2008-07-15
I've installed amula 2.2.0 when I used 7.10, then I upgraded to 8.04 , and now I uninstalled amule from synaptic.
apparently , when I type 'man amule' I get the man pages of this version , how to completely remove amule?

---

### Post by Ryadt on 2008-07-15
Did you delete the .amule folder in your home directory (it's hidden)?

---

### Post by chrisccoulson on 2008-07-15
You can completely remove amule by doing the following:
```
sudo apt-get --purge remove amule amule-common
```

---

