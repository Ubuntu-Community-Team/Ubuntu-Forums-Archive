---
title: "ACPI shutdown bug = freaky HDD sounds"
date: 2005-02-26
forum: Hardware &amp; Laptops
---

### Post by Lord Sandwich on 2005-02-26
My eMachines system refuses to power down properly with ACPI enabled, and simply sits at "acpi_power_off called".

What's troubling is that the system appears to be improperly cutting off power to the hard drive, because it produces a loud CLICK (like with an old HDD that's approaching failure), followed by a whining engine-like sound.

Right now I'm resorting to simply rebooting and hitting the power button once the GRUB menu appears. Does anyone know if this is safe from a hardware perspective?

---

### Post by Lord Sandwich on 2005-02-26
Also, I've tried the "acpi=off"+APM method, but although it does shut down my system the clicking sound is still there. And I lose sound support this way.  :?

---

### Post by Manuzzi on 2005-03-02
[QUOTE=Lord Sandwich]My eMachines system refuses to power down properly with ACPI enabled, and simply sits at "acpi_power_off called".

What's troubling is that the system appears to be improperly cutting off power to the hard drive, because it produces a loud CLICK (like with an old HDD that's approaching failure), followed by a whining engine-like sound.

Right now I'm resorting to simply rebooting and hitting the power button once the GRUB menu appears. Does anyone know if this is safe from a hardware perspective?[/QUOTE]

Have the same symtoms. We are going to (almost) give away 15 old computers with the Ubuntu distribution installed. Most likely the new owners never saw a Linux machine before. So, it's a pity the systems hangs after Power down and hangs after reboot or restart. After another reboot it doesnot hang anymore.

Tried all the solutions from the topic  "Problem on shutting down computer from Ubuntu".

gr, Herman

---

### Post by Wombat on 2005-03-02
Manuzzi,
I don't have an answer for your hard drive noise,but if you want the system to shut down auto.I had the same problem until I downloaded the hoary linux-image 2.6.11.1-K7 kernel now it shuts down auto.If you are using warty,you have to change your sources.lst names from warty to hoary and update in synaptic and find the kernel install it and then change your sources.lst back to warty and run update again.Now I used K7 as I have althon cpu,you could use i396 ,but hoary version.The only problem I had with the new kernel was I can't get my printer to be auto reconized,but if I reboot back to the old warty i386 kernal I left in grub,it is reconized and works.So I hope this helps and maybe someone will read this and answer my problem.
Wombat

---

### Post by Lord Sandwich on 2005-03-02
As it turns out, the clicking/wheezing sound has disappeared. It's possible I may have mistakenly left APM on during my numerous shutdowns.  8-[ 

I heard the next kernel release addresses ACPI issues, though. Here's to hoping for a successful power_off!

---

### Post by Manuzzi on 2005-03-03
[QUOTE=Wombat][...]If you are using warty,you have to change your sources.lst names from warty to hoary and update in synaptic and find the kernel install it and then change your sources.lst back to warty and run update again.Now I used K7 as I have althon cpu,you could use i396 ,but hoary version.[...]
Wombat[/QUOTE]

Where do I find sources.lst ?

---

