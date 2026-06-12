---
title: "wireless problem"
date: 2008-09-14
forum: General Help
---

### Post by bradpurvis on 2008-09-14
i am having a problem with my wireless. i am on a 1 year old lenovo N100 3000. i have been on wireless internet on this before and it suddenly stopped working. i have enabled the restricted drivers and stuff like that. the network manager stopped showing my belkin54g router and now i am on my desktop instead of my laptop

---

### Post by Sycron on 2008-09-14
type on laptop: ```
sudo iwlist scan
```

---

### Post by pytheas22 on 2008-09-14
Please post the output of the command in the post above, as well as this:
```

lshw -C Network
lspci -nn
dmesg | grep -e wlan -e eth1 -e error -e iwl -e bcm -e b43 -e ssb -e ath
```

---

### Post by bradpurvis on 2008-09-14
that didn't help

---

### Post by pytheas22 on 2008-09-14
> that didn't help

Those commands aren't supposed to fix the problem; they provide information for us to see so that we can figure out what's wrong.  Please open a terminal, run the following commands and post the output here:

```
iwlist scan
lshw -C Network
lspci -nn
dmesg | grep -e wlan -e eth1 -e error -e iwl -e bcm -e b43 -e ssb -e ath
```

---

### Post by bradpurvis on 2008-09-14
you know what, never mind i fixed it myself

i'm on i right now:)

---

### Post by Sycron on 2008-09-15
Could you say what was the problem?

---

