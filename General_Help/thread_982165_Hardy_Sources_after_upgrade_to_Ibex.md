---
title: "Hardy Sources after upgrade to Ibex"
date: 2008-11-14
forum: General Help
---

### Post by Merovius on 2008-11-14
Can anyone tell me if a system I upgraded to Intrepid from Hardy should have only Hardy sources under the Third Party tab? There boxes are checked.

The only Source I see listing Intrepid is for security.

On my system that was clean installed all sources show as Intrepid.

TIA

---

### Post by taurus on 2008-11-14
You can look at your /etc/apt/sources.list to see if everything is pointing to intrepid.

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Merovius on 2008-11-16
This is what shows under the third party tab.

[ATTACH]92906[/ATTACH]

Shouldn't it show the Intrepid sources instead of Hardy. In past upgrades it has done this.

---

