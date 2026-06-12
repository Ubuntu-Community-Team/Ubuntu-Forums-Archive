---
title: "Update manager shows updates that apt-get doesn't show"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by Sprax on 2009-01-17
Choosing "check" from the update manager tells me there are 8 available updates. Running "sudo apt-get update" and then "sudo apt-get upgrade" tells me there are no available updates. What's up?

---

### Post by taurus on 2009-01-17
Maybe you want the 

```
sudo apt-get dist-upgrade
```

---

### Post by Sprax on 2009-01-18
No I don't want a dist upgrade, that's an entirely different thing. I'm talking about regular upgrades. Plus I'm running 8.10. Also I think the "dist-uprade" command doesn't work anymore for whatever reason. At least it didn't work on another computer that's running 8.04.

---

