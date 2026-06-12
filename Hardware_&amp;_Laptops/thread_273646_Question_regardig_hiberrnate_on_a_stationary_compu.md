---
title: "Question regardig hiberrnate on a stationary computer"
date: 2006-10-08
forum: Hardware &amp; Laptops
---

### Post by haffe on 2006-10-08
Hello. The computer in question is an old one with an nforce2 motherboard. Getting suspend2 to work is a major pain. However, on my nforce4 motherboard, hibernate seems to work out of the box, is there a way I can make my nforce2 computer to work similliarily?

---

### Post by bizzaroMike on 2006-10-08
I'm having similar problems.  A couple or three of my observations:

1) If you install "hibernate", you'll get the suspend2 hibernate script which can do suspend-to-ram, suspend1 and suspend2 jobs, but it has some hardware hacks to help things along.  When I installed that on my VIA EPIA, I could do "sudo hibernate" and get it to suspend1 hibernate.  You'll have to edit /etc/hibernate.conf to enable this, as well as adding "resume=/dev/hdd-with-swap/" to the /boot/grub/menu.lst file on the kernel line.  Still, this isn't slick.  I tried to edit /etc/acpi/ stuff to have it hibernate when the power button is pressed, but no success yet.

2) I'm too lazy to build a suspend2 kernel, but I have had one in gentoo (where such things are easier) and it was nice.  Good suspend and resume support.  I wish it was the default in Ubuntu.

3) I wish details like hibernate weren't flagged as laptop features.  It makes it hard to enable them.  I'd like to have suspend as a "logout option" in KDE, but that doesn't seem to be possible.  

Hope some of this helps.

---

