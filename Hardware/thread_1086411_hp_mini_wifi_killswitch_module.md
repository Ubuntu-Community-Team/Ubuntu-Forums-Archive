---
title: "hp mini wifi killswitch module?"
date: 2009-03-04
forum: Hardware
---

### Post by eikenberry on 2009-03-04
I have a hp mini 1030NR with the HP mie/ubuntu setup installed on it as well as debian. I'm trying to figure out which bits of software make the wifi killswitch on the front work. It works fine in mie/ubuntu but I can't get it working in Debian. 

I'm fishing for advice. Anyone have any ideas on what makes that switch work? Thanks.

---

### Post by weboide on 2009-03-12
You need the hpmini kernel module installed (on MIE, it is given by linux-ubuntu-modules.)
I'm trying to build a package (for intrepid, and maybe other ubuntu/debian releases) that will contain this module, but I'm not an expert at packaging kernel modules.

---

