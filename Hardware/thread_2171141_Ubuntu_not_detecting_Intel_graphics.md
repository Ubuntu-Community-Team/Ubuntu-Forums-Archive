---
title: "Ubuntu not detecting Intel graphics"
date: 2013-08-29
forum: Hardware
---

### Post by TheSqueak on 2013-08-29
My desktop machine has an Ivy Bridge i7 processor, which should have HD 4000 integrated graphics on it, but Ubuntu doesn't appear to detect it at boot.

```
$ lspci | grep VGA
07:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 640] (rev a1)
```

Is it possible to use both the nvidia card and the intel card at the same time, and if so, why would it not be being detected?

---

### Post by Yellow Pasque on 2013-08-29
Look in your BIOS for Optimus options.

---

### Post by TheSqueak on 2013-08-29
> **Temüjin said:**
> Look in your BIOS for Optimus options.

Aah, apologies, I should have been clearer. It's a desktop, not a laptop, but the nvidia card only has 2 dual-link DVI outputs and i'd like to use the Intel one at the same time so that I can drive 3 large displays

---

### Post by Mark Phelps on 2013-08-29
You won't be able to use both the Intel and Nvidia video chips at the same time.

---

