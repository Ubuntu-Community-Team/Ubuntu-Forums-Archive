---
title: "Finding make / model information"
date: 2008-10-22
forum: Hardware
---

### Post by QwUo173Hy on 2008-10-22
I'm trying to find the model number of my laptop or some other info so I can order parts, but there's nothing on the laptop. Is there any linux tool that might find some info somewhere in the computer and share the knowledge with me? It's a Hasee brand.

---

### Post by prshah on 2008-10-22
> **jarlath said:**
> I'm trying to find the model number of my laptop or some other info so I can order parts, but there's nothing on the laptop. 

lshw will tell you everything you need about the actual hardware; try running it as superuser ```
sudo lshw
```

Many manufacturers put model information and details into the BIOS.. see if you have any such information in your CMOS setup screen.

---

### Post by QwUo173Hy on 2008-10-22
Thank you prshah!

---

