---
title: "QLogic 2300 excessive kernel messages"
date: 2009-02-28
forum: Hardware
---

### Post by mgandalf on 2009-02-28
I'm running Ubuntu desktop 8.10 using a QLogic 2302 connected to an EMC Clarrion via fibre. I'm getting excessive DEBUG() and DEBUG2() messages from the kernel:

> scsi(0): [R|Z]IO update completion.

Does anyone know how to turn these off?

Thanks, Mark.

---

### Post by mgandalf on 2009-03-01
Nevermind.. seems it was fixed by going to RIO mode 5 instead of 6 under "firmware extended options" in the card's BIOS.

- Mark.

---

