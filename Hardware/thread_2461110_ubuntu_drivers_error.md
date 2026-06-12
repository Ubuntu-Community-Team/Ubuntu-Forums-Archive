---
title: "ubuntu drivers error"
date: 2021-04-24
forum: Hardware
---

### Post by linerman on 2021-04-24
Hi,

I wanted to upgrade my nvidia-driver (from 455 to 460), so I ran 

```
sudo ubuntu-drivers autoinstall
```

I got error[INDENT]```
WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level

```

That is strange, because I have never installed nvidia-driver-390.
But further:
```

Some packages could not be installed. This could mean
that an impossible situation was requested or an unstable distribution was used
in which some packages have not yet been created or moved
from the Incoming directory.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  nvidia-driver-460: Requires: nvidia-kernel-source-460 (= 460.73.01-0ubuntu0.20.04.1) but it will not be installed
E: Could not fix problems, corrupt packages stopped.

```
[/INDENT]

---

### Post by CelticWarrior on 2021-04-24
Try:

```
sudo apt-get remove --purge nvidia*
sudo ubuntu-drivers autoinstall
```

---

### Post by The Cog on 2021-04-24
I'm guessing you may need quotes round that asterisk to stop it expanding to anything starting with nvidia:
```
sudo apt-get remove --purge "nvidia*"
```

---

### Post by CelticWarrior on 2021-04-24
> **The Cog said:**
> I'm guessing you may need quotes round that asterisk to stop it expanding to anything starting with nvidia:
```
sudo apt-get remove --purge "nvidia*"
```

But we want to uninstall everything Nvidia...

---

### Post by andrewlorien on 2021-05-04
Without the inverted commas, bash tries to expand the * to anything in the scope of the current commandline.  And probably finds nothing, unless you've been downloading some nvidia resources to help you fix your graphics card.
With the inverted commas, the search "nvidia*" is passed to apt, and it is expanded there - and the packages are removed.

worked on my machine!

---

