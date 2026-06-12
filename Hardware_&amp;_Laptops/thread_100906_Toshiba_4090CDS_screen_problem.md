---
title: "Toshiba 4090CDS screen problem"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by omeg on 2005-12-08
**Problem:**
On a Toshiba Satellite 4090CDS, when starting any version of Ubuntu (either Live or a full installation), there is a strange graphical glitch at the bottom of the screen.
[LIST][*][Example image #1](http://omega.avalanchestudios.net/personal/dropbox/ubuntu_problem_1.jpg)
[*][Example image #2](http://omega.avalanchestudios.net/personal/dropbox/ubuntu_problem_2.jpg)[/LIST]

I tried booting up with the **vga=771** parameter for "old monitors", but while this did fix the strange graphical glitch at the bottom, it spawned whole new glitches (see [here](http://omega.avalanchestudios.net/personal/dropbox/ubuntu_problem_3.jpg) and [here (the top and bottom bars are missing, rendering the system useless)](http://omega.avalanchestudios.net/personal/dropbox/ubuntu_problem_4.jpg)).

The laptop's specifications - Toshiba Satellite 4090CSD:[LIST][*]400 MHz Celeron
[*]128 MB SD-RAM
[*]2.5 MB VRAM[/list]

Note that this laptop is still in good shape and is able to run Windows 98 perfectly without any graphical errors. It seems that X on Linux is the only thing that has ever given me these sort of problems.

I hope that you guys are able to help me!

EDIT: I think I might have better posted this in the laptop sub-forum. Sorry about that.

---

### Post by daller on 2005-12-09
What graphiccard does it have?

Please add your pc here:

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba)

... A  Satellite 4090CDT is also mentioned!

---

### Post by omeg on 2005-12-13
I fixed the problem now. The problem was that the system forced on a resolution that was beyond the graphic card's capabilities. It knew that 800x600 was the LCD's native resolution, but didn't realize that forcing depth 24 would surpass the 2.5 MB VRAM.

Forcing it to use depth 16 fixed this completely.

(I added this to [HardwareSupportMachinesLaptopsToshiba](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba).)

---

### Post by daller on 2005-12-14
Nice! Thanks!

---

