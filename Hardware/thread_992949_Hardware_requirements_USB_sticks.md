---
title: "Hardware requirements USB sticks"
date: 2008-11-25
forum: Hardware
---

### Post by Tony Thijs on 2008-11-25
Hi,
I want to use an USB stick to boot Ubuntu from. I saw an announcement of a Kingston 64 GB datatraveler (DT 150) USB stick.

Are there known requirements for USB sticks for use with Ubuntu to achieve adequate performance?
Kind regards,
Tony Thijs
Oriolus Publishing

---

### Post by snowpine on 2008-11-25
Ubuntu will run from a 1gb device as a Live USB, or a 4gb (or larger if you want room for your data) device as a full install. Intrepid Ibex has a new tool for creating a Live USB. Or, if you want a full install, just use the regular installer and make sure you install Grub to the correct device (not your internal hard drive).

I've installed several different flavors of Linux on USB devices. They are always much slower than a hard drive install. Also, you have to make sure your computer's bios supports a boot from USB (many older computers do not).

Hope that answers your inquiry; let me know if you have any specific questions.

---

### Post by timcredible on 2008-11-25
a friend installed ubuntu on an 8gb generic flash drive, and it was annoyingly slow (windows would grey out waiting for a response from the flash drive).  another friend installed ubuntu on a sandisk 4gb microsd card with a usb-to-microsd converter and it worked pretty well (no grey windows).  so, i guess it depends on your definition of adequate performance - looks like it'll work on just about any flash drive, but the faster the read/write times, the better.  i don't have the specs on either of the drives i mentioned, unfortunately. i'm assuming here you intend a normal install of ubuntu, not the livecd install.  for a livecd install, i did that to a kingston 1gb drive ($6) and it's about the same speed as a CD (not something you'd want for a normal install).

---

