---
title: "Disabling discrete card in a desktop computer"
date: 2011-08-24
forum: Hardware
---

### Post by lishi on 2011-08-24
Hello :

i have a sandy bridge processor (2500k) with a z68 motherboard and a nvidia discrete graphics (560).

Now : Under windows i run lucid virtu that will switch between the integrate and the discrete depending on the application. I know that that is not going to work in linux. So i plan to just use the integrated VGA only.

this is the situation i have :
```

lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF110 [GeForce GTX 560 Ti] (rev a1)

```

It's working out of the box, but before leaving as it is i have few question. 
Should take further step to disable the discrete card, its quite a powerhog and the fact the nouveau documentation say that power management is still unsupported for my model dont help.

---

