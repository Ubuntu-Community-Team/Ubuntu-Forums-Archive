---
title: "Kubuntu 9.10 on Dell D620; locking up after closing lid"
date: 2009-10-18
forum: Hardware
---

### Post by diamond on 2009-10-18
This is really annoying.

I have a Dell D620, and I upgraded to Karmic about 2 weeks ago. Everything has been running fine so far, but a new problem just popped up today. If I close the lid, it is supposed to lock the screen (I have it set that way on all Power Management profiles just to be sure), but now it seems to just lock up entirely. When I open the lid, the screen is dark and there is no response at all from the keyboard or the mouse. I can't even switch to a new virtual terminal (i.e., Ctrl+Alt+F2, etc.).

The machine isn't dead; I can SSH in. But I can't interact directly with it at all; it acts as if the keyboard and mouse are just disconnected. I have to do a hard reboot (or halt it through SSH) to get it to work again.

Does anyone have any idea what the heck is going on? Has anyone encountered this before? I did get a whole truckload of updates yesterday, but I don't remember what they were.

Please help; this is driving me nuts.

SOLVED: The problem was the setting in Guidance Power Manager. It was set to "Do Nothing" when the lid is closed. I set it to "Lock Screen", and that fixed it.

---

### Post by dlight on 2009-11-05
I have this same exact problem---however I am running Gnome.

I don't have the option to "lock screen" on lid close. I have the options "BlankScreen", "Suspend", "Hibernate" or "ShutDown".

This happens when I have "BlankScreen" selected. 

Anyone have any ideas? or, does anyone know what script is executed when "BlankScreen" is selected and the lid is shut?

---

### Post by dlight on 2009-11-05
Ill add that when I set it to "Suspend" it works as expected. The laptop blanks the screen, suspends, and then when opening the lid later it will resume properly.


The problem is I need applications to continue to run when the lid is shut---and only suspend when the power button is pressed.

---

### Post by kees-tux on 2009-11-06
I have a simular effect with my _desktop_. After logging out, but keeping the machine running overnight, when I arrive back I have the same symptoms.
If I restart kdm over the network (ssh) my kdm-screen lit up but not keyboard and no mouse response.

From remote shell(ssh) "hexdump -C /dev/gpmdata" show that my mouse is still working. :mad:

---

