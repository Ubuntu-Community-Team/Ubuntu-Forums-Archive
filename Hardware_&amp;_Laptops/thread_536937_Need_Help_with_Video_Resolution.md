---
title: "Need Help with Video Resolution"
date: 2007-08-28
forum: Hardware &amp; Laptops
---

### Post by mikesena on 2007-08-28
Hi,

I have been trying to get my laptop to use a 1280x1024 resolution, with 75mhz refresh rate, but each time i try to apply it, it crashes.  (i am on kubuntu, but its not strictly related to that).  My laptop is a toshiba a50 satellite, with an integrated intel graphics.  i was using i810 as the device, i changed that to intel and installed the device as described.  i also installed the xorg intel driver.  it works fine with 1024x768, but i would like the larger resolution.

it keeps crashing.  can anyone help me figure out why this is happening please?

---

### Post by OttifantSir on 2007-08-28
A little more information on your hardware and OS would be nice, but you might try this: (Reading from the Official Ubuntu Book to give this piece of advice that MIGHT and might NOT work)

Find out which kernel you have. If you don't have a GRUB boot menu, reboot and hit Enter when you see GRUB on-screen. You should have at least two choices. One main-boot and one recovery. What's the number on these two? If they end in -15, you might try going to Synaptics, hit Reload and then Mark All Upgrades. That will get you the newest kernel. At least if you have 7.04 Feisty Fawn, I haven't used 6.06 and 6.10 that much. You will need to reboot the machine after that.

This MIGHT help, it might NOT. I'm a newb, it's just that someone posted something similar in another thread and at least one of them had the -15 kernel. I posted there a few minutes ago, so I don't know if this will work. It's just something that seems right in my head. New Driver, Old Kernel=Crash. New Driver, New Kernel= Might NOT crash?

If you already have the newest kernel, hope someone else has a better answer for you.

---

### Post by raijinsetsu on 2007-08-28
Getting that resolution out of an IGP... I dunno... Especially the intel chipset.
See [this post]("http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+950+resolution"). It might be what you're looking for.

---

