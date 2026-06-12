---
title: "the command to manually switch on/off fans on dell I9400?"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by Brachabre on 2006-08-18
hello, this might've been already asked....but i searched already for this and came up dry.

Is their some sort of command to manually switch on/off the fans on my dell I9400?

I downloaded i8kutils and gkrellm    but don't know how to use i8kutils through it...

---

### Post by yeehawjared on 2006-08-24
did you ever figure this out?

---

### Post by smelly_sox on 2006-08-25
With gkrellm installed, start it and alternate click on the top border.
This will provide you with options: configuration, theme, & quit.
Select configuration.
In the left hand column select plugins
Enable DELL i8kplugin
In left hand column select arrow next to plugins to display sub-menu.
Select DELL i8k Plugin
In the main window now select display both fans
Both fans should now be displayed on the gkrellm desktop window.
Simply by clicking on the fans you can change their state between manual off/low/high (& auto I think).

Otherwise open a temrinal, and enter
*i8kctl fan*
This will tell you the states of your fan/s. I have 2 on my DELL C640 so I get *0 1* when the main fan is running on low. 0 for off, 1 for low, & 2 for high. So if you want manual control to put both fans off *i8kctl 0 0* both fans high *i8kctl 2 2*. For more information *man i8kctl* in a terminal.

Sorry I didn't see this post sooner.
Regards

---

