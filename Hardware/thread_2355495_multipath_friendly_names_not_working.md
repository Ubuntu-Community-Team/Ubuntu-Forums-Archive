---
title: "multipath friendly names not working"
date: 2017-03-13
forum: Hardware
---

### Post by jlorberblatt on 2017-03-13
I have a ubuntu 16.04 machine with a iscsi multipath volume, which connects correctly:

my multipath.conf looks like this:
defaults {
	user_friendly_names yes
}
blacklist {
	devnode "^vd[a]$"
}

yet when I connect to the device I only get the raw WWID for volume in /dev/mapper instead of the more usable /dev/mapper/mpath[n] name that user_friendly_names is suppose to create.
Anyone have any ideas?

All of this is working with the same steps in a previous LTS release of ubuntu.

---

