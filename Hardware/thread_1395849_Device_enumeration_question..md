---
title: "Device enumeration question."
date: 2010-02-01
forum: Hardware
---

### Post by Objekt on 2010-02-01
When a machine has multiple devices of the same type, how does Ubuntu choose enumeration?  I have two gigabit NICs (Marvell 88E8056) built in to the motherboard, which Ubuntu designates eth0 and eth1.  eth0 plugs into my LAN, but eth1 isn't connected to anything.

(FWIW, Ubuntu 9.10 64-bit.  Motherboard is an Asus P5E3 WS Pro.)

Under Windows XP, the designation is the opposite.  The active NIC is called "Local Area Connection" and the unused one "Local Area Connection 2."  So I'm curious about how Ubuntu numbers things.

---

### Post by IcarusR on 2010-02-02
Linux always starts it's numbering with 0 whereas windows starts with 1.

---

### Post by Objekt on 2010-02-02
Oops, typo in original post.  I meant to say the active connection (eth0 in Ubuntu) gets labeled "Local Area Connection 2" by Windows XP, while the inactive one (eth1 in Ubuntu) is #1 (or just "Local Area Connection").

---

