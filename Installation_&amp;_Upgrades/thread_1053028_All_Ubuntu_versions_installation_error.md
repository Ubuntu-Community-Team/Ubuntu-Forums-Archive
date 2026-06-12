---
title: "All Ubuntu versions installation error"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by kbloem on 2009-01-28
Hello,

i've downloaded all Ubuntu versions and every version has the same problem.

I've got a Asus M2N-MX motherboard and a Nvidia 7600GS. I've read a lot about driver problems and updates but that is not the problem for me.

When i boot with the installation CD i see the menu options. Then i select "install Ubuntu" and from there on i see the progress bar run with the ubuntu logo above it. But when it enters the actual setup i get a scrambled screen. So i thought, ok a driver issue.

Then i tried a safe mode installation and i also have the same problem. Does anyone got any alternatives for me? 

I also have an option to install with a drivers disc but i don't know how to do that. I'm relatively new to Ubuntu so i need some help.

Thanks!

---

### Post by kbloem on 2009-01-28
Kick

---

### Post by avtolle on 2009-01-28
It does look like a graphics card issue to me, from your description of the trials and tribulations you have gone through. Which version are your currently trying to install? 

One thing I would recommend; use the alternate install iso burned to CD. This uses a text based installer, and avoids at least some of the problems with the graphical installer on the Live CD with certain cards. You may download the alternate install iso from the same place you got the others, scroll down the page and look for "alternate" (on the 8.10 download page, IIRC it is on the right more than half-way down the page).

---

### Post by kbloem on 2009-01-29
Thanks,

i&#7743; trying someting else now. I&#7743; installing Ubuntu using my onboard VGA. After that i want to install the new 180? drivers of nvidia and hope they work. Clearly the driver included in the 8.10 standard iso have an issue with my videocard. 

For now i&#7743; keeping my fingers crossed and hope the new drivers will work.

If anyone has any other suggestions, they are more than welcome....

---

### Post by kbloem on 2009-01-29
Ok here is what i did....

I installed using the onboard VGA. After that i went to [www.nvidia.com](www.nvidia.com) and downloaded the 180.22 driver.

Then i went to the shell and killed X with sudo killall gdm

Then i installed the driver i downloaded with sh NVidia.......

After that i went back to my BIOS and changed my adapter to PCI-E.

While booting my Ubuntu logo was still looking messed up so i thought it didnt solve anything. But when i got to the logon window everything was ok.

I am relatively new to Ubuntu so i don't know a lot but is it possible my shell still uses the 173 or 177 driver from Nvidia for booting before it gets into gnome?

How can i update my shell with the new driver?

---

