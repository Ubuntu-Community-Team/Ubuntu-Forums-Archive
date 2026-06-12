---
title: "Hibernate on lid close.."
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by robfindlay on 2005-09-25
Can someone tell me how to make the lid close event cause a hibernation?

---

### Post by robfindlay on 2005-09-26
[QUOTE=robfindlay]Can someone tell me how to make the lid close event cause a hibernation?[/QUOTE]

BUMP... 


Can someone help me on this? 



Rob

---

### Post by JLB on 2005-09-26
This applies to my HP laptop. Yours should be the same/similar... My personal preference is sleep. Its much faster.

To get the lid switch to activate suspend to RAM, edit /etc/acpi/events/lidbtn and change "action=/etc/acpi/lid.sh" to "action=/etc/acpi/sleep.sh"

To get the lid switch to activate suspend to DISK, edit /etc/acpi/events/lidbtn and change "action=/etc/acpi/lid.sh" to "action=/etc/acpi/hibernate.sh"

---

### Post by robfindlay on 2005-09-26
[QUOTE=JLB]This applies to my HP laptop. Yours should be the same/similar... My personal preference is sleep. Its much faster.

To get the lid switch to activate suspend to RAM, edit /etc/acpi/events/lidbtn and change "action=/etc/acpi/lid.sh" to "action=/etc/acpi/sleep.sh"

To get the lid switch to activate suspend to DISK, edit /etc/acpi/events/lidbtn and change "action=/etc/acpi/lid.sh" to "action=/etc/acpi/hibernate.sh"[/QUOTE]


Thanks man that did it!

---

### Post by JLB on 2005-09-26
no problem :)

have you made up a wiki page on your laptop?  it would be helpful to the rest of the community to know and help make ubuntu the best laptop distro out there.

Regards!
JL

---

### Post by P_Squiddy on 2005-09-27
Sounds like that's all well and fine for an HP laptop, but should the same work for any laptop?  Specifically, I'm using a Toshiba Satellite A70, which has a few glitches but otherwise works very well.  Selecting Hibernate when logging off seems to just hang the machine, so I'm leary of trying the above solution for closing my lid (not that this is my preferred action anyway).  Should hibernate work for all laptop models in about the same manner?

---

### Post by Elv13 on 2005-11-13
ACPI dont really work with A70, only battry

---

