---
title: "HP deskjet 1000 j110"
date: 2013-12-26
forum: Hardware
---

### Post by heplerwd on 2013-12-26
hi

running 10.04. need driver for hp deskjet 1000 j110 usb port. tried hplip-3.13.11.run - didn't work.
thanks

---

### Post by tgalati4 on 2013-12-27
Open a terminal:

```
hp-toolbox
```

Set up the printer and print.

---

### Post by Yellow Pasque on 2013-12-27
New versions of hplip are going to be difficult to get for Lucid since it's so old (you'll run into dependency problems as you discovered...).

According to HP's site, you need hplip >= 3.10.9 and Ubuntu Lucid/10.04 only has 3.10.2 by default. Try this PPA to get an easy install of hplip 3.11.1: [https://launchpad.net/~till-kamppeter/+archive/ppa](https://launchpad.net/~till-kamppeter/+archive/ppa)

---

### Post by heplerwd on 2013-12-27
need a printer driver for hp deskjet 1000 j110. tried hplip-3.13.11.run didn't work. ubuntu sees printer tells me what it is and that it is on usb but won't print.

---

### Post by mörgæs on 2013-12-27
Please stop multiposting. You have already been informed that 10.04 is too old, so you should go for a fresh install of a recent Buntu release.

Threads merged.

---

