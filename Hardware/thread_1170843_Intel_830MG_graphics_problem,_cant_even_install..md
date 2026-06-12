---
title: "Intel 830MG graphics problem, cant even install."
date: 2009-05-26
forum: Hardware
---

### Post by talbain on 2009-05-26
Hello, i have an old japanese laptop (Fujitsu Lifebook FMV-6100MG2 [Specs {Japanese} here: [http://www.fmworld.net/biz/fmv/product/hard/blb0204/spec_mg.html]](http://www.fmworld.net/biz/fmv/product/hard/blb0204/spec_mg.html])) with an Intel 830MG graphics chipset, im trying to install Jaunty on it but the show stops when the boot disks tries to go into graphical mode, all video output goes crazy, can see lots of colours and lines, but nothing usable, i had this same problem before with Edgy and to solve it, i think i installed in text mode and edited the xorg.conf for it to use another intel driver (i910?) but i dont remember the details, nor could i find the thread i used as a guide in UbuntuForums about 2yrs ago, but now in jaunty, xorg.conf is empty so i dont really know what to do.

Can anyone help me out? please?

Edit: Tried xfix and then added option "Driver i910" to xorg.conf, didnt work :(
Edit: Maybe its trying to boot in an unsupported resolution/refresh rate?

Edit: Ok, everyone, nevermind, looks like intel dropped support for the linux i830mg driver... or something like that, i give up.

---

