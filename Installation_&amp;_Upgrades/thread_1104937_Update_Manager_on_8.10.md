---
title: "Update Manager on 8.10"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by alphacrucis2 on 2009-03-24
A few days ago, I noticed when an update notification appeared and I started it, update manager offered to do a partial upgrade. It appears to be related to the Filezilla package from backports but update-manager just terminates if I tell it to do the partial upgrade. If I cancel the partial upgrade it seems to process other package upgrades fine as at least two have come through since this started happening. The partial upgrade seems to be to do with  two filezilla packages from backports which show greyed out if I cancel the partial upgrade. Can anyone shed any light on what I need to do to sort this out.

Thanks

---

### Post by alphacrucis2 on 2009-03-24
> **alphacrucis2 said:**
> A few days ago, I noticed when an update notification appeared and I started it, update manager offered to do a partial upgrade. It appears to be related to the Filezilla package from backports but update-manager just terminates if I tell it to do the partial upgrade. If I cancel the partial upgrade it seems to process other package upgrades fine as at least two have come through since this started happening. The partial upgrade seems to be to do with  two filezilla packages from backports which show greyed out if I cancel the partial upgrade. Can anyone shed any light on what I need to do to sort this out.

Thanks

OK. I tried uninstalling filezilla using the synaptic package manager and then reinstalled it. This has fixed the problem. Hey still learning this stuff:lolflag:

---

