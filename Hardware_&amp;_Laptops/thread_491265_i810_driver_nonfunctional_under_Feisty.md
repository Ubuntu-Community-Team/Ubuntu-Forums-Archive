---
title: "i810 driver nonfunctional under Feisty"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by 043087m135 on 2007-07-03
Hey all

Edgy was running fine on my Pavilion N5495. I even had some basic desktop effects working with Gandalf's AIGLX. I upgraded to Feisty and now it blackscreens after loading. I also get a strange white pattern on my screen when I startx from the rescue CLI.

lspci reports my VGA controller as such: Intel Corporation 82830 CGC [Chipset Graphics Cotnroller] (rev 03)

I can start the system with the vesa driver but I have to time it correctly, because if I wait too long after startx then it blacks out using vesa too. I have to use the keyboard combination to switch video outputs. I think that that might be the problem...this system has been a bit finnicky with external monitors and the tvOut. BUT EDGY WAS WORKING GREAT, WHAT HAPPENED?

Can I roll back the intel driver packages to the edgy versions? Is there a different way to fix this, short of reinstalling Edgy?

Thanks!

---

### Post by Aninhumer on 2007-07-05
I have been experiencing similar problems, but the only way I can get my laptop display working, even with vesa, is to plug in an external monitor, switch to it, and then back again.
This makes the laptop useless for any kind of mobile use.

Do the old versions of i810/intel work correctly, and is it possible to use them instead?

---

### Post by NilsE on 2007-07-05
Try replacing the i810 driver with the intel driver in synaptic.  It will uninstall i810 but you can reverse it if it does not help by then installing the i810 driver.

---

### Post by Aninhumer on 2007-07-05
When using the intel driver, x will not start claiming that there are no screens with a usable configuration (I have tried changing the bitdepth, but it did not help).

If i recall correctly the i810 driver would start but there would be no output even with an external monitor.

---

### Post by 043087m135 on 2007-07-07
> **Aninhumer said:**
> I have been experiencing similar problems, but the only way I can get my laptop display working, even with vesa, is to plug in an external monitor, switch to it, and then back again.
This makes the laptop useless for any kind of mobile use.

Do the old versions of i810/intel work correctly, and is it possible to use them instead?

What I know is that Ubuntu Edgy worked wonderfully, and I could set it up with an external output to the TV. It was perfect, just about (couldn't figure out how to get xinerama working, although combined desktop works under windows - so i know the hardware can do it).

---

