---
title: "Agere Modem Driver"
date: 2008-11-08
forum: Hardware
---

### Post by spiritfox on 2008-11-08
I recently got a computer with a lucent/agere systems modem (discovered using linmodems.org's scanmodem tool).  I'm using 8.10 (kernel 2.6.27), so the 8.04 tarball available from their site (at [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)) doesn't work because it's the wrong kernel version.  When I try to follow the instructions there to compile one from source, i get to the point where it tells me to 
         "1. Use your favourite PLAIN TEXT editor, such as vi or gedit, and with root permission. This file is typically located at /usr/src/linux/sound/pci/hda/hda_codec.c
         2. Add the lines EXPORT_SYMBOL(snd_hda_codec_read); and EXPORT_SYMBOL(snd_hda_codec_write); to the file, after the list of '#include' statements in the beginning.
         3. Save the file."
That file does not exist.  Does it exist anywhere?  if not, is there another way to install the driver?  I've used ubuntu for about two years, and I'm good with all the superficial gnome and bash stuff, but anything into the deeper recesses of the kernel and I'm lost.

---

### Post by spiritfox on 2008-11-09
*shameless bump*
I really do need help on this.  anyone?

---

