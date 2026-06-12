---
title: "Help Reset Password On Laptop"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by Mavis on 2007-11-17
Cannot get into my laptop computer as cannot reset password.  It said password was incorrect, don't know why as it is the only one I had!  So tried to reset but nothing happens.  Have clicked reset password is there anything else that I can click on the keyboard that will do this?  Hope someone can help me thanks.

Mavis

---

### Post by aysiu on 2007-11-17
Boot into recovery mode (it's the boot option right below the normal one).

Then type ```
passwd *username*
``` where *username* is your actual username. For example, if your username is *mavis*, you'd type ```
passwd mavis
``` to reset your password. Then type ```
sudo shutdown -r now
``` to reboot. Then select the normal boot option.

---

