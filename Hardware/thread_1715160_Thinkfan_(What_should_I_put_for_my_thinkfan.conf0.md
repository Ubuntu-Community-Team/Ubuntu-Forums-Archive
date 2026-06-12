---
title: "Thinkfan (What should I put for my thinkfan.conf0?"
date: 2011-03-26
forum: Hardware
---

### Post by emtdan on 2011-03-26
I installed thinkfan but when I run it the fan doesn't stop.  

Here is what I have

sensor /proc/acpi/ibm/thermal (0, 0, 10 ,1,  0, 0, 10, 0, 10, 10, 5, 5, 0, 0, 0 )

(0,   0,   40)
(1,   38,   45)
(2,   39,   50)
(3,   43,   54)
(4,   45,   55)
(5,   48,   56)
(6,   50,   67)
(7,   57,   500)



What should it be?

---

### Post by emtdan on 2011-03-26
It actually now goes up and back down but never stays in one spot...  Does it have to do with my sensors being set wrong?

---

### Post by Allmighty_Lulala on 2011-07-03
I have the same problem like emtdan!

Does anyone know any solution?

---

### Post by tgalati4 on 2011-07-03
I have a T43P with a noisy fan.  I tamed it two ways--undervolting, (which entails recompiling the kernel and turning P-States Voltage Control to "On") and running tpfan-admin.  You have to play around with the values.  On my system, my CPU stays around 47-49C consistently and the fan speed speeds up and slows down rhythmically (due to hystersis) but maintains the CPU within a narrow band.  When compiling a kernel (which takes 1 to 2 hours) the fans are full blast and the CPU is pegged at 74C.

Because the ATI GPU and Pentium M CPU share the same heatsink and fan system, the fan goes on and off at random times because you have two heat sources triggering the fan speed.  You can change the set points to whatever you want, but eventually something will trigger that fan and set it off.  The workarounds basically keep the fan running at low speed (15%) which is much less bothersome or off or some combination between the two.

It's not obvious, but outside temperature seems to make little difference.  The heat sink is well-designed and it removes heat in cold or warm conditions equally well.  It's just that in hot weather the rest of the machine heats up so it has more trigger points to set the fan off.

---

### Post by Allmighty_Lulala on 2011-07-04
> **emtdan said:**
> It actually now goes up and back down but never stays in one spot...  Does it have to do with my sensors being set wrong?


I finally got it working. I had the same problem. But for me the help was uninstalling thinkpad fan control (if you installed it) and maybe the help was also installin "laptop-mode-tools"

---

