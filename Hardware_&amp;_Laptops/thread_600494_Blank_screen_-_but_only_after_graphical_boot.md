---
title: "Blank screen - but only after graphical boot?"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by Bramo on 2007-11-02
Hi, I'm running Ubuntu Studio (Gutsy version) on a Dell Latitude D400.

Recently I replaced the 'intel' graphics driver with the 'i810' driver as closing my laptop lid was hanging the computer and that's the only solution I could find.

Using the i810 driver I was getting a blank screen after the usplash graphical boot finished. It took a while to pin this down as after a couple of reboots I hit 'Alt+F1' to see if I could see any errors and of course things went fine. Finally the penny dropped. I removed the 'splash' option from the relevant kernel line in /boot/grub/menu.lst

It boots fine now.

When hitting Alt+F1 previously it gave me errors relating to the resolution, but I updated /etc/usplash.conf to be 640x480 (which is what it was falling back to) and that didn't help.

In hindsight I never got a graphical boot under PCLinuxOS either, but I never had a problem with the newer 'intel' driver and the Ubuntu Studio graphical boot.

Does anyone know how I could fix my sexy Ubuntu Studio boot splash with the i810 driver or am I stuck having to choose between graphical boot and not hanging when I close the lid (not a tough choice really)?

---

