---
title: "how do I make MAUSB-10 with 8.04"
date: 2008-05-16
forum: Hardware
---

### Post by cigtoxdoc on 2008-05-16
How can I get Olympus MAUSB-10 USB reader/writer to work with 8.04 LTS?

John

---

### Post by PhilippeP on 2008-06-10
What does says *dmesg* when you plug the device ??

Open a terminal, type *dmesg* ...
Plug the device, wait a few seconds
type *dmesg* in terminal again ...

---

### Post by NM5TF on 2008-12-30
> **PhilippeP said:**
> What does says *dmesg* when you plug the device ??

Open a terminal, type *dmesg* ...
Plug the device, wait a few seconds
type *dmesg* in terminal again ...

I am having the exact problem that John is with 8.10 Intrepid....

typing *dmesg* indicates the device is recognized correctly and that
the Alauda interface driver loads, but the device refuses to mount and I
can't get my pix from the card.

Any ideas???:confused:

Tom

---

