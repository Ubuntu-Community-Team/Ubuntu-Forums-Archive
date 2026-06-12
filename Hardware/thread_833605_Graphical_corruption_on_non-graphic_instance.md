---
title: "Graphical corruption on non-graphic instance"
date: 2008-06-18
forum: Hardware
---

### Post by Maverick1712 on 2008-06-18
Hey all

Just installed 8.04 on my HP Pavillion. When I press Ctrl+Alt+F1 to get toa non-graphical instance, I get vertical lines of varying colours. The only instance that works for me is the graphical one. Using lspci I see my graphics card is  VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE). I am using the ATI restricted driver. Please let me know where I should be looking for the cause of this issue.

Cheers,
Maverick1712

---

### Post by pietjanjaap on 2008-06-19
you can try this, but proberly you have the wrong driver.



dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

