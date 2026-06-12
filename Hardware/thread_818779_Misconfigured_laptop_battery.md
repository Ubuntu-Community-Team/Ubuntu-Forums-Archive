---
title: "Misconfigured laptop battery"
date: 2008-06-04
forum: Hardware
---

### Post by bdoe on 2008-06-04
I have a strange problem with Ubuntu 8.04 with regards to my laptop battery. When I click on its properties, it shows that the battery is fully charged, but is only operating at 69% capacity.

Here's the details: Battery properties shows that my battery has a design charge of 88.8Wh, and a current charge and last full charge of 62.0Wh, resulting in a capacity rating of only 69% (poor).

When I physically inspected the battery, I saw on the label that it is a 62Wh battery. Therefore Ubuntu is mis-reading my battery configuration. Is there a way to correct this so that it shows the correct design charge and, therefore, the correct capacity rating?

---

### Post by sdennie on 2008-06-04
That information should be coming from the laptop BIOS so, it's possible that a BIOS update might correct it.  You should also see if you can check the battery charge from within the BIOS to see if it agrees with what Ubuntu is saying.

---

