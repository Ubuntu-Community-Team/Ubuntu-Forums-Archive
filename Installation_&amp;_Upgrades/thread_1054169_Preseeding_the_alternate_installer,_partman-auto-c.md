---
title: "Preseeding the alternate installer, partman-auto-crypto and LUKS"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by dagriff on 2009-01-29
Hi,

We currently have a custom built CD that installs Ubuntu 8.04 using a preseed file in the initrd to deploy our desktops.

I would like to extend this to laptops, but am coming up against a lack of documentation for the debian installer preseeds regarding LUKS.

Ideally we would want:
[LIST=1]
[*]The install to ask for a user passphrase
[*]A second LUKS key get added automatically to allow for key recovery
[*]Whole partition encryption, whilst allowing the user to resize the existing windows partition.
[/LIST]

From what I've tried so far I can resize and encrypt with a passphrase manually, but not via preseeds. If the second key has to be added outside of the installer process that's not a problem, the install and configuration has a second phase managed via cfengine.

---

### Post by junk408 on 2011-02-16
Were you ever able to get the answer to this?  I'm trying to figure it out as well.

---

