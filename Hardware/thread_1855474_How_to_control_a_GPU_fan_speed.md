---
title: "How to control a GPU fan speed?"
date: 2011-10-06
forum: Hardware
---

### Post by mibart on 2011-10-06
Hi,
I have AMD Radeon HD5770 graphics card (ASUS if that matters). The problem is incorrect behavior of the GPU cooling fan. This fan runs always at full speed, regardless of GPU load. It makes my PC sounds like a starting jet-plane. I use open-source ati driver, no FGLRX. What can I do?

Needless to say, that under MS Windows GPU fan runs correctly, I mean slow and silent when GPU is not working hard.

Maybe there is some software to control a GPU fan? Any suggestions?

---

### Post by gordintoronto on 2011-10-06
What version of Ubuntu are you using?

You might install lm-sensors. At minimum, you would be able to see the GPU's temperature.

---

### Post by mibart on 2011-10-07
It turned out that installing FGLRX driver (from restricted drivers) solved full speed fan issue. Now, the fan of my graphics card behaves exactly as under MS Windows. Anyway I still wonder if there is possible to control fan speed when using open source ati driver?

---

