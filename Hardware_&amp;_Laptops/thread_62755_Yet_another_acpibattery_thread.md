---
title: "Yet another acpi/battery thread"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by cbudden on 2005-09-05
Hello.

As you could guess, my battery monitor is reporting "system is running on battery power, status unknown".  I would like it to not say this, but to say what it should. 

Some details
I have a Acer 4500
/proc/acpi/battery and /ac-adapter have no files/folders in whatsoever.

I have tried adding acpi=force in grub but this didn't help.

I have read on other threads about SBS.  This sounds likely to work but im not sure about recompiling the kernel.  What other things does this affect?

thanks

Chris  :)

---

### Post by cbudden on 2005-09-06
bump

---

### Post by briguy on 2005-09-06
Did you try this? [http://www.ubuntuforums.org/showthread.php?t=49045](http://www.ubuntuforums.org/showthread.php?t=49045)

---

### Post by cbudden on 2005-09-06
[QUOTE=briguy]Did you try this? [http://www.ubuntuforums.org/showthread.php?t=49045](http://www.ubuntuforums.org/showthread.php?t=49045)[/QUOTE]
 My laptop is not listed in the repositary, so do you think that using one that is close to the model number will work?

---

### Post by briguy on 2005-09-07
Hmmm - don't know.  You might contact Acer and they might be able to tell you how close it is.  You could try to fix it yourself if you're ambitious, or submit  your current dsdt to the good folks at acpi4linux.

If your notebook is really new product, it might be a short while until somebody posts the fixed dsdt -  it will come though.  Too bad Acer hasn't started coding the dsdt properly yet.

---

### Post by cbudden on 2005-09-07
I sent Acer a email about the battery not working properly so maybe they will send a good DSDT.

---

### Post by snop on 2005-09-07
[QUOTE=cbudden]I sent Acer a email about the battery not working properly so maybe they will send a good DSDT.[/QUOTE]

Yes... sure...

The only solution comes from patching your kernel or your dsdt (take a look at [https://sourceforge.net/projects/sbs-linux/](https://sourceforge.net/projects/sbs-linux/)) and/or acpi linux mailing lists.

SnOp

---

