---
title: "HP Pavilion dv9000 - Touchpad stop working"
date: 2010-08-22
forum: Hardware
---

### Post by Kajoo on 2010-08-22
Hi, I got laptop HP Pavilion dv9000 and few days ago after I turn on laptop I had notice that touchpad doesn't working. I don't know what's happened tbh just stop working. I got also another OS installed and check it under Windows 7 and touchpad working without any problems. I'm using Ubuntu 10.04.

---

### Post by mesilikas on 2011-09-18
Hello exactly the same problem I also have same laptop with a HP Pavilion DV9541ev
 The problem starts from the moment I do login and then display the user selection is operating normally the touchpad
Friends please your help :p

I'm using Ubuntu 10.04 32bit

---

### Post by mesilikas on 2011-09-26
Well the problem is now history followed the instructions here: [https://help.ubuntu.com/community/SynapticsTouchpad]("https://help.ubuntu.com/community/SynapticsTouchpad")  
and unity: **Touchpad not working after login** use the following command in the console:
[HTML]gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true[/HTML]
and my problem is now history! ):P

---

