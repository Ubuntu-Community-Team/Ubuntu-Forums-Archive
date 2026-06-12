---
title: "Small CLI ubuntu for one purpose"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by valnar on 2009-09-08
I want a Linux distro to run within a VMware session and it needs to do only one thing - run the [rinetd]("http://www.boutell.com/rinetd/") program.  I could probably get by with DSL or Puppy, but I don't have the time to learn another distribution.  That is still an option though, if somebody had an easy way of doing it (with included binaries for network access, etc.)

Would I just use the server edition to do this?  I don't need the GUI to run.  Is there a lighter-weight ubuntu than the server edition, without any other crap?

---

### Post by Mighty_Joe on 2009-09-08
[Ubuntu JEOS]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos") is targeted specifically for VM's.

---

### Post by Fafler on 2009-09-08
Try Debian. Scripts made for Ubuntu should work on Debian on most cases.

BTW, what can rinetd on a virtual machine do that iptables on the host can't?

---

### Post by valnar on 2009-09-08
> **Mighty_Joe said:**
> [Ubuntu JEOS]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos") is targeted specifically for VM's.

That's what I needed.  Thanks.

---

