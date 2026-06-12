---
title: "Two video cards mess"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by xcarol on 2006-12-13
I have two video cards installed on my computer, one agp and one pci, and although it is bios configured to be agp the main video card, all the text console terminals (tty1-tty6) appear on the pci screen even if I start with recue mode with no X. How could I change that? I am using Kubuntu Edgy. It doesn't happen with Kubuntu Hoary.

Thanks a lot.

---

### Post by xcarol on 2006-12-18
I found it!
The file /etc/modules contains an entry with: *i2c_matrxfb* commented that line and everything went bac to normal. But now I cannot use de PCI Video Card :( 
So, I think there is no way to get the virtual terminals in the nVidia AGP card with the Matrox PCI active.

---

