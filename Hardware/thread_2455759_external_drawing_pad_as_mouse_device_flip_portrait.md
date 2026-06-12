---
title: "external drawing pad as mouse device: flip portrait - landscape"
date: 2020-12-26
forum: Hardware
---

### Post by phorminx on 2020-12-26
I have an external drawing pad (digimemo l2) that's recognized as a mouse device and works fine with xournal. My only problem is: it assumes landscape.  How can I switch to portrait? (I am running xubuntu 16.04.)

---

### Post by Holger_Gehrke on 2020-12-27
You can set the Coordinate Transformation Matrix for your tablet using xinput. See [this page]("https://wiki.ubuntu.com/X/InputCoordinateTransformation") in the Ubuntu Wiki for the details.

Holger

---

### Post by phorminx on 2020-12-27
Thank you, the page from the Ubuntu Wiki was exactly what I needed.

---

