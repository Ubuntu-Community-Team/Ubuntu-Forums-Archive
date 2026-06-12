---
title: "Brother 110c on 8.04"
date: 2008-09-17
forum: General Help
---

### Post by dgoodma on 2008-09-17
The steps to install the lpr and cups driver on the Brother site for the 110c printer did work previously, but do not seem to work on 8.04. Did the structure change to support printing? Any suggestions on making this printer work?

---

### Post by plucky on 2008-09-17
> **dgoodma said:**
> The steps to install the lpr and cups driver on the Brother site for the 110c printer did work previously, but do not seem to work on 8.04. Did the structure change to support printing? Any suggestions on making this printer work?

The brother printer drivers are now packaged in Synaptic.

See this [link](https://wiki.ubuntu.com/BrotherDriverPackaging) for information about Brother Driver Packaging.

Good Luck

---

### Post by phidia on 2008-09-17
Unfortunately there's a recurring bug [here]("https://bugs.launchpad.net/ubuntu/+source/cupsys/+bug/35638") that seems related (note the updates to the bug which affect hardy).

I don't have that printer but if it was working and then stops after a new install or upgrade (which did you do BTW?) then you kind of have to consider it may be a bug.

If you did an upgrade you might try a clean install or wait for the release of 8.10.

---

