---
title: "ATI Radeon HD 4500 not recognized"
date: 2013-11-15
forum: Hardware
---

### Post by kondilidisn9 on 2013-11-15
Hi I'm kind of new to Ubuntu-Linux. I installed ubuntu 12.04 LTS and my ATI Radeon HD 4500 is not recognized by the system... I searched everywhere but I didn't find a way out...
Thank you in advance.

---

### Post by Yellow Pasque on 2013-11-15
If you're referring to "unknown graphics" in the info center, see: [https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

If you're looking for proprietary drivers, there are none available for that card. The open-source driver is installed/used by default.

If you're referring to something else, please be more specific. Posting or pastebin'ing the /var/log/Xorg.0.log could be helpful in that case.

---

### Post by heir4c on 2013-11-15
What you mean by: "not recognized by the system"?
Go to SystemSettings and than 'Details'. What stands next to "Graphics"?

---

### Post by QIII on 2013-11-15
Hello.

Just a bit of background so you understand what is going on here.

AMD/ATI moved all cards HD 4000 and earlier to a "legacy" branch and no longer actively develops the driver that will work with them.  Up through Ubuntu 12.04.1, this was not an issue.

From 12.04.2 (which you likely have installed) forward, changes to the kernel and X Server have occurred and the legacy driver will no longer work.

Canonical has not dropped support for your card, ATI has.  However, the open source driver installed with Ubuntu by default will still work.

You may see instructions for hacks to get the legacy proprietary driver to work with more recent versions of Ubuntu, but I would *very, very strongly *recommend ***against*** using them.  They effectively break your Ubuntu by downgrading your graphics environment and making patches to the kernel.

Best wishes.

---

### Post by Jason.e.kemp on 2013-11-15
So just out of curiosity is it the same for the HD 5000 as well?

---

### Post by QIII on 2013-11-15
For the time being, HD 5000 series and later are still supported.

---

### Post by deadflowr on 2013-11-15
> **Jason.e.kemp said:**
> So just out of curiosity is it the same for the HD 5000 as well?

No.
The HD 5000,6000, and 7000 + are still supported by ATI/AMD.

To the OP, are you using the card?
If yes, then Ubuntu recognizes it. 

If by unrecognized, you mean that it lists as unknown there is a package called mesa-utils which will make it show the card/driver info.
But it's unnecessary to install, because it won't change anything about the cards functions.

---

