---
title: "Checking The Computer Specs"
date: 2010-08-23
forum: Hardware
---

### Post by Th3Blaze on 2010-08-23
Im on Ubuntu Luicid and was wondering how to view the computer specs. I.e the Complete CPU name (Ex. Intel E7400 @ 2.8 ghz not Core2duo @ 2.8ghz) 
and the GPU.

Thanks In Advance

---

### Post by Th3Blaze on 2010-08-23
Is there anything else I need to put?

---

### Post by cascade9 on 2010-08-23
"sudo lshw" 

You're going to get a lot more info that just the CPU and GPU, ut it does give you tthe output you wanted...model numbers, not generic "Core2Duo 2.8GHz" etc. Here is a tiny example of what I get- 

> 
*-cpu
          description: CPU
          product: AMD Phenom(tm) II X2 550 Processor

*-display
                description: VGA compatible controller
                product: G98 [GeForce 8400 GS]

---

