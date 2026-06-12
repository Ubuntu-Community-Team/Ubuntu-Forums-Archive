---
title: "Suspend on lid close fails, works otherwise"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by ububug on 2007-10-20
Hi,
I installed a fresh install of Gutsy yesterday on a HP nx6110 laptop (915 chipset). Everything works, except the computer does not suspend on lid close (actions in gnome-power-manager are set). Worked fine in Feisty. Suspending manually from the menu works fine. Could someone point me, please, to some relevant reading or give me advice where to look for info? What are the relevant logs?
thanks. Jiri

---

### Post by Diabolis on 2007-10-20
After upgrading to gutsy I couldn't suspend. Then I found this thread: [http://ubuntuforums.org/showthread.php?t=471855&highlight=gutsy+suspend](http://ubuntuforums.org/showthread.php?t=471855&highlight=gutsy+suspend) and I installed **uswsusp**. Now I can suspend through the GUI or by typing the appropriate command in the terminal, but not by closing the lid.

Acer travelmate, intel chipset

---

### Post by shadilac on 2007-10-22
Same problem on Compaq Presario v6000. I also installed uswsusp, suspend still only works when open. Hibernate didn't work before or after, but at least now it gives me an error and doesn't crash my machine.

---

### Post by Diabolis on 2007-10-23
Finally I fixed it. :) this is very easy to fix, just go to power management preferences and set the action that you want to be performed when the lid is closed lol. I assume that after upgrading from fesity to gutsy the power management settings are set to default (blank screen).

---

