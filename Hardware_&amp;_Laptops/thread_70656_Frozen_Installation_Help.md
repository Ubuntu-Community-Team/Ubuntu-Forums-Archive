---
title: "Frozen Installation Help"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by misterquickly on 2005-09-30
I completed an installation of Ubuntu from the cd-rom. My laptop then rebooted and started unpacking everything from the hard-disk. It looked like things were going fine until the process froze at this screen:
 
"add user: Warning: the home dir you specified already exists.
Adding system user 'gdm'...
Adding new user 'gdm' (104) with group 'gdm'
Home directory '/varlib/gdm' already exists
*Reloading GNOME Display Management Configuration
*Changes will take effect when all current X sessions have ended.

invoke- rc.d: init script gdm, action "reload" failed.

Setting up gnome-games (2.10.0-Obuntu2)..."

I'd appreciate if anyone could help me figure out what to do now because I need this laptop for schoolwork...

---

### Post by Mustard on 2005-09-30
Did you do a default install or an expert install?

Did you use any special install options?

---

### Post by az on 2005-09-30
Boot into recovery mode and run

apt-get -f install


Also, what version are you using?

---

