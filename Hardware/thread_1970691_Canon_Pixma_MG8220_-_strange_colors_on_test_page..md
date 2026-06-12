---
title: "Canon Pixma MG8220 - strange colors on test page."
date: 2012-05-01
forum: Hardware
---

### Post by Lubelaczek on 2012-05-01
I have this fairly new printer Pixma MG8220. It works under 12.04. However test page printed using general settings (everything is "default") shows very strange colors. Everything is darker than I would expect. For example yellow is more like brownish than yellow. Under "windowza" prints fine. It is not issue related to inks being mixed or dirty print head. Anyone experience something similar?

---

### Post by aikishugyo on 2012-05-04
> **Lubelaczek said:**
> I have this fairly new printer Pixma MG8220. It works under 12.04. However test page printed using general settings (everything is "default") shows very strange colors. Everything is darker than I would expect. For example yellow is more like brownish than yellow. Under "windowza" prints fine. It is not issue related to inks being mixed or dirty print head. Anyone experience something similar?

Hi, the gutenprint driver, if that is what you are using for your MG8200 family printer, is not tuned, so certainly the colors may be somewhat off. At the moment there is no method to tune printers colors except for feedback from users. Perhaps you could adjust the various color density settings yourself in CUPS and see if you can get better results, and then let me know what adjustments worked for you.

Regards,
Gernot Hassenpflug
Canon backend maintainer for the gutenprint project

---

### Post by Lubelaczek on 2012-05-06
I had it set to RGB color model. Simple change to CMYK solved my problem. I am not talking about fine tuning since this may need little more and deeper investigation to achieve desired results. I think this thread may be closed as solved.

---

