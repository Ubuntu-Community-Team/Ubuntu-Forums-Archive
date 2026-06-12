---
title: "Port replicator for Dell M90 will not use DVI cable"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by Jefferson Heard on 2006-12-06
Hi all.  I have an interesting problem with a Dell port replicator on the M90 portable desktop.  X will only use the VGA cable to my monitor if I am docked.  If I simply plug the DVI cable into the laptop it works fine, of course, but plugging in everything manually is kind of a pain. This is true while using the monitor standalone and while using it as a second screen a la Xinerama.  Booting into Windows, I can use the port replicator to attach via DVI without a flaw, so it's not the port replicator's problem.  I am using the nVidia beta driver, but I get the same problem with vesa and nv drivers.

Any ideas?

---

### Post by elpcat on 2007-03-27
I had the same problem, and had to define  the DFP's in my xorg.conf file.

    Option         "UseDisplayDevice" "DFP-0, DFP-2"
    Option         "ConnectedMonitor" "DFP-0, DFP-2"

Im pretty sure that DFP-1 is the vga port on the replicator.

Later!

---

