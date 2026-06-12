---
title: "Sound"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by Dr. Z2A on 2005-09-19
Ok I first off I do not use Ubuntu any more, I'm on Gentoo.  The reason I posted this here is because Ubuntu is the only distro ive tried on my laptop that I have gotten the sound to work in.  I am pretty sure that I have a Conexant sound card.  I was thinking I should probably find out what Ubuntu has differently in its sound that most other distros so I can figure out what I have to do to my Gentoo machine.  Can anyone help me out here?

---

### Post by bernardfrancois on 2005-09-28
If u re-install ubuntu, then you can check the driver loaded for the sound card using **lsmod**.

If you copy the driver file to the right directory on your gentoo system (/lib/modules/.../kernel/drivers/sound ; this directory path can vary), then you can load the driver temporary (for testing) using the **insmod** command. If it doesn't work, you can still try to load different drivers from the above mentioned directory, untill you found one that works (you don't need to reboot, just use the insmod command to install one (driver) by one (and tes each time)).

If you found a working driver, you can add it to the /etc/modprobe.conf (name may vary, other names like conf.modules or modules.conf are possible).

In addition to just loading all those drivers, you might also have to enter additional information about your sound card (like IRQ nrs, channels, ... - which you can see in bios or the datasheets of your sound card). You can do this using lines starting with 'options' in the modprobe.conf file. But offcourse, you can check the modprobe.conf file of the ubuntu installation.


I just copied the above information from my notes I took yesterday at school... They were talking about installing network interface cards, but I kinda changed it to sound cards... I think they are installed the same way, so you can try...

---

