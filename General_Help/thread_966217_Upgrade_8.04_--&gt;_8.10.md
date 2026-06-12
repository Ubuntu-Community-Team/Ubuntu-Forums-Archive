---
title: "Upgrade 8.04 --&gt; 8.10"
date: 2008-11-01
forum: General Help
---

### Post by hlein on 2008-11-01
Hi,

If I update Ubuntu installed by Wubi from 8.04 to 8.10, do I have to update Wubi too? If yes, what is the procedure? Will my existing Ubuntu get lost?

Thanks for your help

Regards
Helmut

---

### Post by grinias on 2008-11-01
> **hlein said:**
> Hi,

If I update Ubuntu installed by Wubi from 8.04 to 8.10, do I have to update Wubi too? If yes, what is the procedure? Will my existing Ubuntu get lost?

Thanks for your help

Regards
Helmut

Same question here...

---

### Post by ajwak95 on 2008-11-01
You shouldn't have to, just go to System->Administration->Updates and down by where it says "Release Upgrade" change it to Normal Releases instead of Long Term Support Releases. Then open up a terminal and do ```
sudo apt-get update
```

---

### Post by rhcm123 on 2008-11-01
> **ajwak95 said:**
> You shouldn't have to, just go to System->Administration->Updates and down by where it says "Release Upgrade" change it to Normal Releases instead of Long Term Support Releases. Then open up a terminal and do ```
sudo apt-get update
```

No, apt-get update does not update the system, it just updates the package listings. very different; Apt-get does not install the upgrades.

after doing the first part of what he said, (changing the relase upgrade to normal)
go to administration -> update manager. Click the upgrade button near the top and you'r off to the races.

sources, with much better instructions:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

