---
title: "Battery Recalibration"
date: 2009-11-29
forum: Hardware
---

### Post by fcourier on 2009-11-29
I recently rebuilt a lithium-ion battery for my acer laptop by replacing all of the cells. Unfortunately, the battery needed recalibrated for the new capacity to be recognized. My laptop manufacturer didn't provide any type of functionality to do this in the BIOS (Acer). 

So at first, I tried running down the battery in the BIOS screen after a full charge. This didn't recalibrate the battery at all. I then tried to set the gnome-power-manager's settings for critical power to do nothing (actually I had to set it to nothing in gconf- editor). Again, the last full capacity didn't change.

Eventually, I had to reinstall windows and perform 4 full discharges/recharges for the new full capacity to be reflected. I then reinstalled ubuntu.

The Question:

Is there a way to perform battery recalibration in ubuntu/linux. The manufacturer specifies to fully charge, fully discharge and then recharge the battery. I assumed this meant setting the critical battery action in gnome-power-manager to "do nothing" and then just waiting for the battery to run down. However, the last full capacity didn't change after several tries when I actually did this. I assume this means that I'm overlooking something on either discharging the battery fully, or I'm assuming that linux would change last full capacity value and it doesn't. Any help would be appreciated.

P.S. I'm positive that the laptop supports ACPI (Acer Aspire 6920) if that helps to narrow this down.

---

### Post by Soapy.Illusions on 2009-12-11
I have the exact same laptop and exactly the same problem, except I bought a new battery not skilled enough to rebuild it

At first it would not calibrate properly now it just constantly says its at 0% even when I know there is a charge


I would hate to have to reinstall everything please tell me you have a better solution...

---

