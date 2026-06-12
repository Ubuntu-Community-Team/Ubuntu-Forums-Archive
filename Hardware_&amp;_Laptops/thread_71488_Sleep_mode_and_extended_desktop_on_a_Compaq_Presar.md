---
title: "Sleep mode and extended desktop on a Compaq Presario M2130EA laptop"
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by jonnyc on 2005-10-03
Hello

Last night I installed Ubuntu on my Compaq laptop. Everything went fine and even installed Wi-fi with no bother

2 things I need are a good sleep mode and extended desktop support

I tried editing the "/etc/default/acpi-support" line, but it said it was read only

As for extended desktop, I have no idea where to start. I need to use it for doing presentations with a data projector through normal cable or s-video

Any suggestions?

BTW this is my first ever look at linux!!

---

### Post by JLB on 2005-10-03
[QUOTE=jonnyc]Hello
Last night I installed Ubuntu on my Compaq laptop. Everything went fine and even installed Wi-fi with no bother
2 things I need are a good sleep mode and extended desktop support
I tried editing the "/etc/default/acpi-support" line, but it said it was read only
As for extended desktop, I have no idea where to start. I need to use it for doing presentations with a data projector through normal cable or s-video
Any suggestions?
BTW this is my first ever look at linux!![/QUOTE]

To edit the sleep mode line in the acpi-support file, try this.

open a terminal, then type:

sudo gedit /etc/default/acpi-support

this will let you edit it with root priv's. you won;t get that read only error this way. you received that message because you were editing a system file without the proper permissions to do so. as far as extending your desktop.... there ar other posts in the forums about that. Sorry..  I can't help you out in that area :)

---

### Post by ssck on 2005-10-06
[QUOTE=jonnyc]Hello

Last night I installed Ubuntu on my Compaq laptop. Everything went fine and even installed Wi-fi with no bother

2 things I need are a good sleep mode and extended desktop support

I tried editing the "/etc/default/acpi-support" line, but it said it was read only

As for extended desktop, I have no idea where to start. I need to use it for doing presentations with a data projector through normal cable or s-video

Any suggestions?

BTW this is my first ever look at linux!![/QUOTE]


I need to use a data projector as well.however, when i tried it with my laptop, it was displaying 800 x 600 while my laptop is 1024 x 768

apart from that the function key does not work.in win xp, by pressing the function key, it will put the display onto the data projector.how do i do this in ubuntu ?

---

