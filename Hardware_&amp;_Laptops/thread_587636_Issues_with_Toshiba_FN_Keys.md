---
title: "Issues with Toshiba FN Keys"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by Ambiguity on 2007-10-22
HI,

I am new to ubuntu and so far it has worked well with everything except the FN keys on my Toshiba M40 laptop. I have toshset and fnfx (both were installed by default with 7.04) but neither one of them work. I upgraded to 7.10 and they are still broken. Today I upgraded my BIOS to the latest version, but that doesn't seem to have changed anything. I am fairly sure that it is a Toshiba Bios, since I have seen that that is the only type fnfx and toshset work with.

~$ sudo toshset
required kernel toshiba support not enabled.

~$ sudo fnfxd
FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could not open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).

~$ sudo modprobe toshiba
FATAL: Error inserting toshiba (/lib/modules/2.6.22-14-generic/kernel/drivers/char/toshiba.ko): No such device

:~$ sudo modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device

I am not sure if I need to recompile the kernel, that is my next thing to try but I am a little hesitant since I have not done that before. Any help is appreciated. Thanks.

---

### Post by Ambiguity on 2007-10-23
I have also tried installing omnibook mentioned here:

[http://ubuntuforums.org/showthread.php?t=562681&page=2](http://ubuntuforums.org/showthread.php?t=562681&page=2)

but when I try:

sudo module-assistant install omnibook

I get:

Package omnibook-source was not built successfully, see /var/cache/modass/omnibook-source*buildlog*

The directory  /var/cache/modass/ is empty though...

---

### Post by Ambiguity on 2007-10-23
I found out the problem with installing omnibook. It needs to be built first which was not mentioned on the page I read. 

Use:

sudo module-assistant build omnibook

I can now change brightness, bluetooth, and wifi, but I do not know how to get fn keys working. I know the scancodes for my fn keys but that is about it...

I would also like to use the Power Manager Brightness Applet to change my brightness if that is possible.

---

### Post by quique1hn on 2007-10-27
I have an omnibook and it´s the first time that this work for mi, tks. :lolflag:

   1. Download the omnibook-source deb from [http://packages.kirya.net/debian/pool/main/o/omnibook/](http://packages.kirya.net/debian/pool/main/o/omnibook/)
   2. Install it using gdebi-gtk or whatever, you may also need to install module-assistant and build-essential
   **3. sudo module-assistant build omnibook**
   4. run sudo module-assistant install omnibook
   5. run sudo modprobe omnibook and voila.
   6. Add omnibook to the bottom of /etc/modules

---

### Post by Ambiguity on 2007-11-02
Still cannot get FN-keys to work. I also discovered that attempting to switch video output to S-video or VGA does not work. 

Luckily after a restart the gnome brightness applet started working and the power manager lets me dim the screen when idle or on battery.

---

### Post by jdos2 on 2007-11-09
I can't get my Toshiba ACPI kernel drivers to load either, "no such device."

My Toshiba is a A215-S7433 (hey, it was a cheap DVD player!). 

I've seen mentioned that if one has the Phoenix bios, the driver won't load. Lemme see...

---

### Post by jdos2 on 2007-11-09
D'oh! Phoenix BIOS. HARUMPH! Now what? My brightness keys worked before... Feh!

---

### Post by livinjean on 2007-11-15
I have satellite a105-s4284 and was having the same problem, then i followed the adivice here ([http://slu.ms/articles/tag/toshiba](http://slu.ms/articles/tag/toshiba)) which got couple of FN keys working under ubuntu feisty, most importantlly the brightness keys.

you can try upgrading your bios and see if it helps.

however, yesterday when i upgraded to gutsy, my FN keys are not working anymore which makes me super mad at the whole phoenix toshiba thing.

---

### Post by angelscrimes on 2007-12-03
hi everybody
i'm a linux newbie and i installed ubuntu gutsy gibbon on a toshiba satellite A60
after several holes in my eyes due to the screen brightness...i tried to install fnfx(not working) and toshset(notworking)

so i tried omnibook as you said and...
it does not work as it should!

i can use some fn key but not the brightness one...

the problem is not the fnkey...i just want to set brightness lower... is there any config to set for omnibook or a command to set brightness down?

Help me please...
..i'm gonna go blind!!!!

---

### Post by angelscrimes on 2007-12-03
one further question:
why the folder /proc/acpi/video/ is empty?

is this the problem?

---

