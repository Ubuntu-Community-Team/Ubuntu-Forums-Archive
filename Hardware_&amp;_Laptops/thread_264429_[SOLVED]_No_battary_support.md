---
title: "[SOLVED] No battary support"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by borobudur on 2006-09-24
Hi everybody, I bought a MSI Mega Book Laptop with a AMD Turion 64 X2 CPU. It's great but there is one things which bothers me. 

There is no battary support. I get any information about the battaries life. Is there a dirver I need to install?

Thanks for your help

---

### Post by xyz on 2006-09-24
You mean you want to see how charged (or not) your battery is?
Not sure!
If so, right click on top panel > Add to panel and look for Battery charge monitor, click on it and then on Add.

---

### Post by borobudur on 2006-09-24
I have done this and I can see the little battary sign but it says that there is no battary.

---

### Post by xyz on 2006-09-24
The battery is of course IN your laptop?

---

### Post by borobudur on 2006-09-25
Yes sir! I'm using it and if I don't take care and the battary is suddenly empty: puff! All gone!! No warning!

---

### Post by ridgerunner7 on 2006-09-25
Sounds like the BIOS isn't giving you good info. I suggest checking MSI for a BIOS update.

---

### Post by Henry Rayker on 2006-09-25
it could be the powernowd or powersaved from synaptics. My laptop required powersaved when i ran on 64b Dapper, but either works in 32b. Make sure you have one of those installed. Without them, my battery info didn't show. They should be in Synaptic by default.

---

### Post by borobudur on 2006-09-27
Changed from powersaved to powernowd. Still the same...
Haven't tried the bios update.

Today I remembered that I had to add the argument **acpi=off** when I installed ubuntu on this laptop. 

What shall I do???

---

### Post by borobudur on 2007-03-14
Found out how to solve the problem!!! :guitar:

After the installation with the acpi=off option, I had to edit the file **/boot/grub/menu.lst**. 

Here I found the **acpi=off **again and this I had to replace with [COLOR=SeaGreen]**nohpet**[COLOR=Black]. [/COLOR][/COLOR]
Now I can use all the battary functionality. Great!

---

### Post by xyz on 2007-03-14
Congratulations on really not giving up easily!

---

### Post by borobudur on 2007-03-16
thanks!

---

