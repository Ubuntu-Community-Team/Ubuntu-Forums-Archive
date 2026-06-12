---
title: "Noob question. Are there problems associated with installing Ubuntu on laptops?"
date: 2010-02-20
forum: Hardware
---

### Post by Darvenkry on 2010-02-20
I'm just wondering if Ubuntu works 100% installing on a laptop? Are laptops any differnet from a typical desktop computer? And specifically, does anyone know if the new HP dv6-2113tx will be compatible with Ubuntu.

---

### Post by bpalone on 2010-02-20
Laptops tend to be different animals, with any Operating System.  Many times they have special one of a kind hardware that there are only drivers for X operating system.  

That said, most of the time you can get most laptops to run Linux.  You may have to scour the internet to find a solution, but usually you can find a solution.  You may also find that you can get everything to work, but one item.  I would recommend using a Live CD to see if everything works before committing to an install.

As for a HP laptop, you will probably be OK.  They do a better job of supporting Linux than many hardware companies.  I don't have any experience with their laptops though, so take this with a healthy dose of salt.

Good luck.

---

### Post by GregBrannon on 2010-02-20
The complaints I see over and over relate to power management and suspend/wake from suspend modes - what happens when the lid is closed and then reopened.  It's hard to tell if these get resolved, or if people just live with them.  I have a Dell that suspends OK but will not wake up.  I haven't tried real hard to fix it, so I've just learned to live with it.

As bpalone pointed out, the hardware on some lsptops can be unique/obscure, so there are also problems with sound, graphics cards, and network drivers.  Most of these are resolved eventually.

---

### Post by bcbc on 2010-02-20
I had issues hibernating... sleeping looked good, but waking up ended up being a normal restart. First problem was my swap wasn't big enough from the default install. Second, when I changed the swap, the new uuid wasn't automatically updated to /etc/initramfs-tools/conf.d/resume

This sort of thing isn't really intuitive... but digging around usually can sort it out.

---

### Post by Darvenkry on 2010-02-20
Oh thx for the replies, very helpful :). And yes i will try live CD or usb before committing to reformattign the harrddrive with linux.

---

