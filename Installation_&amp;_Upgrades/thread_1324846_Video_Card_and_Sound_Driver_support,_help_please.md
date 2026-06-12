---
title: "Video Card and Sound Driver support, help please"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by sawick61 on 2009-11-12
Hello, 
 I have a Radeon 9600xt agp vid card and from other posts i've seen that ATI isn't supporting 9.10 yet.  Any one know how i can maybe use a windows driver on here because my video is sketchy.  My sound isn't very good either and I have an older model MSI mobo "P4MAM2-V" and they don't support linux drivers on their website.  I'm new to Linux so I don't know all the little tricks and configs.

---

### Post by Mark Phelps on 2009-11-12
> **sawick61 said:**
> Hello, 
 I have a Radeon 9600xt agp vid card and from other posts i've seen that ATI isn't supporting 9.10 yet.  Any one know how i can maybe use a windows driver on here because my video is sketchy. 

Linux is not Windows -- you can't use windows video drivers on Linux.

Plus, your card is not supported by ANY of the current ATI drivers -- Linux, Vista, or Windows 7. Plus, there are no plans from ATI to produce any newer drivers for it.  So, it's not going to be supported by ATI in 9.10, either.

In Linux, the open source video driver for Radeon cards will be installed automatically.  That is the only option you will have.

Your best best at this point, with an older motherboard, is to boot from an Ubuntu LiveCD and try the SW out without installing it.  That way you will see how well it detects your hardware and installs the correct drivers.  Anything that does not work is going to range from minor tweaking to outright impossibility to fix.

---

### Post by sawick61 on 2009-11-13
> **Mark Phelps said:**
> Linux is not Windows -- you can't use windows video drivers on Linux.

Plus, your card is not supported by ANY of the current ATI drivers -- Linux, Vista, or Windows 7. Plus, there are no plans from ATI to produce any newer drivers for it.  So, it's not going to be supported by ATI in 9.10, either.

In Linux, the open source video driver for Radeon cards will be installed automatically.  That is the only option you will have.

Your best best at this point, with an older motherboard, is to boot from an Ubuntu LiveCD and try the SW out without installing it.  That way you will see how well it detects your hardware and installs the correct drivers.  Anything that does not work is going to range from minor tweaking to outright impossibility to fix.

incorrect, you can use windows wireless nic drivers sir.

---

