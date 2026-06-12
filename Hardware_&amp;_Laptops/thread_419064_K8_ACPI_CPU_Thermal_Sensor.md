---
title: "K8 ACPI CPU Thermal Sensor"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by Megatog615 on 2007-04-22
In the Hardware Sensors applet, I can select CPU(Under ACPI), and hddtemp sensors to display. The hddtemp sensors work great, and I can read what temperatures my hard drives are at. However, the CPU temperature always stays at 104F, or 40C, which is wrong.

Is CPU temperature for K8(in my case, Athlon 64 3200+) broken, or non-existent?

---

### Post by pragmatine on 2007-04-22
I have the same problem - it seems that the ACPI temp sensor is always at 40C - instead you should make sure the it87 module (at least thats what it is in my case) is loaded so you can use the sensors on your mainboard, and then if you restart sensors applet it should show more sensors which actually work

---

### Post by Megatog615 on 2007-04-22
Do you have an nForce4 SLI motherboard?

---

### Post by pragmatine on 2007-04-24
yes, asus a8n-sli premium to be exact.

---

