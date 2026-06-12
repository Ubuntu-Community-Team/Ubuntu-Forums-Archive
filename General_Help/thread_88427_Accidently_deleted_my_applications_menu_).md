---
title: "Accidently deleted my applications menu :)"
date: 2005-11-10
forum: General Help
---

### Post by mjkelly on 2005-11-10
In the process of installing ntpv, a point of sale program that ive determined is impossible to install, i deleted my applications menu. The Places and System are just fine but when i click on applications all i get is a tiny little tan box thats like 1 pixel x 1 pixel.
So... what im asking is what package restores those menus?

---

### Post by Miguel on 2005-11-10
Well, I guess you could delete all your gnome preferences and then restart gnome. This should work 100% sure if you didn't delete the applications menu as root (or with sudo privileges).

Is your gnome configuration very valuable? Please note that I ask the configuration, not the programs. If you think reconfiguring gnome (and nautilus, and eog, and totem, and all gnome applications) is not too much trouble for you, try to delete the following folders:

~/.gconf
~/.gconfd
~/.gnome
~/.gnome2
~/.gnome2_private

But please note: **[SIZE="4"]THIS IS NOT SUBTLE AT ALL!!![/SIZE]**

A more knowledgeable user would know exactly which folder or file to delete.

You might be asking if this will work. Well, you can check it without deleting anything. To do so, create a new user (no special privileges, just X). Log out and then log in as the new user. If the new user has the default gnome looks with the applications in place, deleting those folders will work. Don't forget to delete the new user after this!

Hope it helps,

Miguel

---

