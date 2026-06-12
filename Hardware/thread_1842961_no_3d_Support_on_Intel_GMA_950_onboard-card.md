---
title: "no 3d Support on Intel GMA 950 onboard-card"
date: 2011-09-12
forum: Hardware
---

### Post by VonSpyder on 2011-09-12
no go on reducing to 16 bit. Ive got a netbook with same GMA950 graphic card and no acceleration at all (no open gl) Ive gone through lucid, maverick, and natty; ive added DRI (which doesnt find anything) and nothing. So if anyone has another idea to make opengl work with this card on ubuntu ide love to hear it.

---

### Post by Toz on 2011-09-13
Intel drivers are a "work in progress" with respect to linux. Have a look at intel's support matrix at: [http://intellinuxgraphics.org/user.html]("http://intellinuxgraphics.org/user.html") for some more information.

Barring anything useful there, you could always try xorg-edgers ([https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")) (I believe they are currently using xserver 1.11). You __may__ get some better performance from those updated drivers.

---

