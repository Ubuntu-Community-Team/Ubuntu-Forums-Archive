---
title: "Razer Taipan buttons not working in Ubuntu 14.04"
date: 2014-05-12
forum: Hardware
---

### Post by Resident_Stevil on 2014-05-12
I have a Razer Taipan mouse which should have 9 functioning buttons (Right, Middle, Left, wheel up, wheel down, 4 side buttons).  The buttons on the sides are working.  The buttons on the left side are responding in xinput as buttons 8 and 9, but the problem is the buttons on the right side are also being recognized as 8 and 9.  I want to get all four side buttons to work as separate inputs.  How do I go about doing that?

---

### Post by Resident_Stevil on 2014-05-14
So I checked the properties with xinput, and it seems there are some unused buttons in there.  Stuff like mouse wheel horizontal left, right, unknown buttons, and so on.  Not sure if any of this affects this issue.  But I am still unable to resolve this and get all the buttons enabled.

---

### Post by hendrik-0 on 2014-09-10
same problem here. i installed razercfg but that does not seem to help. did you manage to solve the problem?

EDIT: Apparently it is the way the hardware is set up (the same issue occurs on windows). The buttons are simply mirrored and are not actually distinct.

---

### Post by r33slive.fr on 2015-01-17
I fix this issue by connecting the mouse on **Windows** system with **Razer synapse**,
Then Razer Synapse update the mouse embed firmware, you have to find friend with windauze (On virtual machine razer synapse can't found the mouse to update it...)

---

