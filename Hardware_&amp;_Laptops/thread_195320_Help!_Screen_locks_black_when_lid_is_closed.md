---
title: "Help! Screen locks black when lid is closed"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by ddumanis on 2006-06-12
Hi,

I have a Dell Latitude C640 with an ATI Radeon graphics card.

It goes black whenever I close the lid. (I have power manager set NOT to put it to sleep on lid-close.) It doesn't seem to be sleeping--the hard drive still runs--it's just black, and moving the mouse, keys, etc. does nothing to bring back the screen.

I have already tried reconfiguring Xserver, although I'm open to suggestions re: trying it again.

Thanks for any and all help!

---

### Post by ddumanis on 2006-06-13
(Update)

I changed back to Screen Lock/Enter Password mode in gconf-editor.

The lid no longer locks up black when I open it (but it makes me enter a password, which is a pain--but whatever).

(Another Update)

After Gnome update on 6/16, we're back to locking up black every time--even with the password screenlock turned on. Yuck.

(Last Update)

Did a complete uninstall on everything ACPI-related, then reinstalled everything. Now it works. Woo-hoo!

---

