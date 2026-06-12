---
title: "Acer Aspire 5020 AMD 64 Turion - installation hangs"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by Booger on 2005-06-07
Hello,

I've got Acer Aspire 5020 notebook. AMD Turion 64 ML-28, Ati Radeon Mobility X700 128MB.

I tried to install Ubuntu 5.04 for AMD64 from CD, but it simply hangs when it comes to choose installation language. Even ctrl-alt-del does not work, I have to turn it off by pressing power-off button for 4 seconds.

What can I do to install Ubuntu?

---

### Post by makro on 2005-06-15
I've the same problem on HP Pavilion zv6069ea. If you plug an USB keyboard the selection language menu works....

---

### Post by GuyveR800 on 2005-06-15
I found that pressing the PrtSc magically enables the keyboard. You will have to press PrtSc once every time you boot into Ubuntu.
Does anyone have an explanation or a solution for this behaviour?

---

### Post by Edd on 2005-06-15
try booting using: **acpi=off i8042.nomux** options at the kernel selection, I had the same problem on my laptop (travelmate 2200) but when i boot with these options the keyboard and touchpad will work.

---

### Post by GuyveR800 on 2005-06-15
Indeed, the touchpad, that's another problem... I can get it to work by doing the following:
rmmod evdev
rmmod tsdev
rmmod psmouse
modprobe evdev
modprobe tsdev
modprobe psmouse

tsdev doesn't seem to be loaded by default tho...

I'm just a n00b, but turning ACPI off sounds kinda scary.

Strangely, I tried the Hoary 32bit LIVE CD and that worked absolutely fine, no keyboard or touchpad problems whatsoever!

---

### Post by giobertox on 2005-11-24
it's just a video-card problem

try :
linux vga=771


ciao ciao ;)

---

### Post by kitsos on 2005-11-24
Hi,
 i have the same laptop/same problem
I solved it by going into BIOS and disabling "legacy USB support". Found the solution on this really good thread about how to get almost everything working on this laptop

[http://ubuntuforums.org/showthread.php?t=46853]("http://ubuntuforums.org/showthread.php?t=46853")

---

