---
title: "Matrox or Ati"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by ruibuntu on 2007-05-11
I have a Matrox g200 millenium Agp with 8 mb and a ATI rage IIC agp also with 8 mb.


Which is the best one for a computer assembled for some production work ( send e-mails, bla, bla) and for watching a DVD once a week?

this choice should include drivers and linux support.

Thx in advance

PS: buying a new card isn't an option.:(

---

### Post by calraith on 2007-05-11
The ATI probably has better support for hardware mpeg2 decoding.  Of course you could just try one card after the other and see which you like better.  Your mileage may vary.

---

### Post by misfitpierce on 2007-05-11
I'd prob have to agree with that

---

### Post by ruibuntu on 2007-05-11
Does anybody know where can i get drivers for this legacy ati card?

---

### Post by calraith on 2007-05-13
> **ruibuntu said:**
> Does anybody know where can i get drivers for this legacy ati card?
I think the appropriate driver would be "atimisc" (probably already installed).  If driver atimisc doesn't work, try killing gdm / kdm, killing X, and in a console, do "sudo X -configure."  Let Xorg tell you what driver it thinks you should be using.  =)

The appropriate driver the Matrox would be "mga" (also probably already installed).

---

