---
title: "Please help with Audigy 2 Value"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by pelikan on 2005-04-26
I followed the sticky, "Hoary Sound Broke," and the Unoffocial Starter Guide sound section. I don't have any sound.

If I open volume control it says, "No volume control elements and/or devices found."

I can see my soundcard in Device Manger, listed as an unknown device.

Thank you in advance for any help you can give.

---

### Post by jdodson on 2005-04-26
[QUOTE=pelikan]I followed the sticky, "Hoary Sound Broke," and the Unoffocial Starter Guide sound section. I don't have any sound.

If I open volume control it says, "No volume control elements and/or devices found."

I can see my soundcard in Device Manger, listed as an unknown device.

Thank you in advance for any help you can give.[/QUOTE]

right audigy 2 value is broken in hoary.  it is due to a problem with the alsa version they shipped.  it will be fixed in breezy.

your options are to either use a different sound device or compile alsa and build it into your ubuntu system.  there might be a backport created in the future to combat this problem.

---

### Post by pelikan on 2005-04-26
Thanks for your reply.

I've been trying to install alsa using the [guide](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=CA0108&module=emu10k1)  from the alsa site. 

When I do this:
./configure --with-cards=emu10k1 --with-sequencer=yes;make;make install

I get an error:
Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/home/f/Desktop/alsa-driver-1.0.8/acore'
Makefile:6: /home/f/Desktop/alsa-driver-1.0.8/Makefile.conf: No such file or directory
make[1]: *** No rule to make target `/home/f/Desktop/alsa-driver-1.0.8/Makefile.conf'.  Stop.
make[1]: Leaving directory `/home/f/Desktop/alsa-driver-1.0.8/acore'
make: *** [install-modules] Error 1

I was, however, able to successfully install the alsa-lib and alsa-utils packages.

---

### Post by pelikan on 2005-04-28
Thanks to [this guide](http://www.ubuntuforums.org/showthread.php?t=19307&page=1&pp=10) I got the sound working. Hallelujah!

---

