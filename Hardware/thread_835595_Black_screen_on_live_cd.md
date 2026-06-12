---
title: "Black screen on live cd"
date: 2008-06-20
forum: Hardware
---

### Post by 01706 on 2008-06-20
Hello

I have got a Fujitsu Siemens AMILO L7310GW which I'm trying to get any linux distribution to work on it but, when the live cd's start they do all there boot stuff then it trys to load the GUI then every thing goes black, I hear the start up sound but dont see anything.

Is there a know problem with linux distributions and this laptop or something im going worng?

---

### Post by loserboy on 2008-06-20
you can try using the alternate text based installer or add boot parameters such as

> noapic nolapic acpi=off

add one or more of those commands to the end of the line when you hit F6... ive been reading that it's prolly not good to use all 3 parameters at once

---

### Post by 01706 on 2008-06-21
I have tryed this and the screen is stall black/blank, when i do Ctrl Alt F1 is displays the text version but i need to get into the GUI version

---

