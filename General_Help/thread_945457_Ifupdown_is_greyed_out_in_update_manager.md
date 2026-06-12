---
title: "Ifupdown is greyed out in update manager"
date: 2008-10-12
forum: General Help
---

### Post by axelsvag on 2008-10-12
After the last update I was left with one package uninstalled and greyed out. I had the same problem on all my machines both with xubuntu, ubuntu and with network manager 0.7 and 0.6. It does not seem to bother the system but somethings seems to wrong.

---

### Post by Yellow Pasque on 2008-10-12
It's probably dependent on a package that's not yet available, so update-manager is "holding" it. As you've noted, this isn't hurting anything. If you want to investigate the exact cause, open Synaptic Package Manager, right-click the package, "Mark it for upgrade" and click Apply. Synaptic should spit out an error telling you why the upgrade isn't doable.

---

### Post by axelsvag on 2008-10-12
Thank you for your answer. I tried your suggestion and the answer is  "Beroende av: netbase (>=4.30ubuntu2) men 4.30ubuntu1 kommer att installeras" It seems like ifupdown is waiting for something new.

---

### Post by axelsvag on 2008-10-15
After the update yesterday it was suddenly possible to make the update for ifupdown and all is fine.

---

