---
title: "Fix: Battery info not working since kernal upgrade .16"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by rhawkes on 2007-06-18
Hi everyone,

Just my little bit of help on a problem that has been bugging me. Since an automatic kernel upgrade (to .16), battery info does not work on my laptop - typing ACPI -v into a prompt shows nothing, and no battery monitoring tools work or power management.

I've found that by pressing escape when prompted to view the GRUB menu on boot up, I can boot back to the .15 kernel where everything works OK. I've since edited /boot/grub/menu.lst (using the command 'sudo gedit /boot/grub/menu.lst) to choose the .15 as my default boot (in my case I had to change the default boot from 0 to 2).

Hope this helps anyone who may have a similar problem.

Now waiting on a proper fix in a later update...!


(sorry if this info has already been posted elsewhere, just took me ages to find and fix!)

---

