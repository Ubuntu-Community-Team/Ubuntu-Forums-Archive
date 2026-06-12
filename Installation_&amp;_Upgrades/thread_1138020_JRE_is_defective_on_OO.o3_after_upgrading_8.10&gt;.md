---
title: "JRE is defective on OO.o3 after upgrading 8.10&gt;9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by paulchinnz on 2009-04-26
OO.o 3.0.1 was working fine on 8.10 for me.

Just upgraded to 9.04 today and after fixing tracker, found the other (more major) problem is that OO.o 3.0.1 is 'broken': every time I open an OO.o document I get a JRE is defective message (see image).

I've tried reinstalling openoffice.org-java-common via Synaptic Package Manager without success.

I can't actually get past the message; clicking on OK just brings up the message again.

---

### Post by paulchinnz on 2009-04-26
Deleted this file javasettings_Linux_x86.xml after finding [this]("https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/31954") and it seems okay now. SOLVED.

---

### Post by mlcourtney on 2009-04-28
It is not solved.  deleting the file had no effect.

---

### Post by washakie on 2009-04-29
Worked for me, but had to delete it out of both:

$HOME/.openoffice.org2/user/config

and

$HOME/.openoffice.org/3/user/config

---

### Post by paulchinnz on 2009-04-29
Thanks for clarifying that washakie. That's what I did as well.

---

