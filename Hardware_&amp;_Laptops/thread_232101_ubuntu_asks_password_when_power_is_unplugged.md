---
title: "ubuntu asks password when power is unplugged"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by hayalci on 2006-08-08
When I pull the power plug out, making the laptop run on batteries, ubuntu asks for my password.
I tried to turn this feature off. I searched all the menus but couldn't find a relevant option for this. Can you point me to the possible source of the problem. 

Thanks in advance.

---

### Post by hayalci on 2006-08-23
I have found the solution,

in gconf-editor, make sure that /apps/gnome-power-manager/lock_use_screensaver_settings is checked, then make sure that in the screensaver settings, lock option is unchecked. This way, it will not ask for password when you pull the plug of your laptop.

[[ I'm surprised that in all my attempts of different configuration options, I manage to set it up as I like during the last test before filling the bug report  :-/ ]]

---

