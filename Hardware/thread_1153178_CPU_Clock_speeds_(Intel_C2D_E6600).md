---
title: "CPU Clock speeds (Intel C2D E6600)"
date: 2009-05-08
forum: Hardware
---

### Post by b3ta on 2009-05-08
Okey, so here is the deal. I have an Intel C2D E6600 on an Asus P5QL Pro motherboard. Last night I clocked my CPU by changing the FSB to 340 to gain 3.07 GHz. In Windows 7 it all works great, clock speed is around 2020MHz idle and under load the clock it's 3070MHz. But when I boot Ubuntu it does show the correct clock speeds, idle 1.60GHz and 2.40GHz which is the original clock speeds. I don't know if the CPU is working at the requested speeds in Ubuntu to but now showing it or if it is working at original speeds... What could be the problem?

Thanks in advance!

//Beta

---

### Post by stchman on 2009-05-08
> **b3ta said:**
> Okey, so here is the deal. I have an Intel C2D E6600 on an Asus P5QL Pro motherboard. Last night I clocked my CPU by changing the FSB to 340 to gain 3.07 GHz. In Windows 7 it all works great, clock speed is around 2020MHz idle and under load the clock it's 3070MHz. But when I boot Ubuntu it does show the correct clock speeds, idle 1.60GHz and 2.40GHz which is the original clock speeds. I don't know if the CPU is working at the requested speeds in Ubuntu to but now showing it or if it is working at original speeds... What could be the problem?

Thanks in advance!

//Beta

I believe Ubuntu simply reads the processor's ID and does not monitor clock frequency.

I have a Core2Quad Q6600 overclocked to 3.0G and Ubuntu still reads it as 2.4G.  The performance is there as I did super PI at 2.4 and 3.0 and it was much faster at 3.0.

---

### Post by b3ta on 2009-05-08
> **stchman said:**
> I believe Ubuntu simply reads the processor's ID and does not monitor clock frequency.

I have a Core2Quad Q6600 overclocked to 3.0G and Ubuntu still reads it as 2.4G.  The performance is there as I did super PI at 2.4 and 3.0 and it was much faster at 3.0.

Oh okey, thats a bit sad. But I am going to try super pi as you did to check. Does anyone know of any application that can monitor the real clock speeds?

---

### Post by b3ta on 2009-05-09
Bump, anyone know such a tool?

---

