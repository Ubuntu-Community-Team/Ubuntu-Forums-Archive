---
title: "External Video on Inspiron 1521 does not work"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by irv on 2008-04-08
I have a Dell Inspiron 1521 and when I plug in a external monitor it does not recognize it. I have a duel boot with Vista, and it sees it when booting with vista but not ubundtu 7.10. The hot keys don't work to switch between the LCD laptop screen and the external monitor. I need to do a powerpoint on Sunday, and I would like to do it in Ubuntu using a projector, but I am afraid it is not going to recognize the projector. I haven't try that yet. I thought if I can get it to see the external monitor it would see the projector. 
Any idea what to try?
Thanks for the help.
Irv

---

### Post by irv on 2008-04-10
Is there anyone out here that has any input on this problem.
Thanks
Irv

---

### Post by DellCA on 2008-04-16
Did you ever get this fixed?

For Dell notebooks you should be able to toggle between internal LCD, external display and both using the Fn+F8 key combination.  This is supposed to be working at a hardware level (motherboard/BIOS) and not dependent on the OS that is running on the system.

What happens when you press Fn+F8 with the external monitor connected and powered on?

Have you tried switching to the external display while booting to Vista, then rebooting into linux to see what happens?

Assuming you are booting straight into X Windows, have you set up the configuration for the external monitor as well as the built in LCD panel?  I've run into problems before when setting up a new monitor under linux where the previous configuration was, basically, out of range for the new monitor so it didn't display anything until the config was updated.

Hopefully this gets you going in the right direction.  If you have any question on the system I'll be happy to answer them.

Larry
Dell Customer Advocate

---

