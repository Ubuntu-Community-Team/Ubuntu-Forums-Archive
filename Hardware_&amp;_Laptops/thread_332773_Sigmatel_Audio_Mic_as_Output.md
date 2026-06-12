---
title: "Sigmatel Audio Mic as Output"
date: 2007-01-06
forum: Hardware &amp; Laptops
---

### Post by Frogger on 2007-01-06
I have a Dell Inspiron B130 with a sigmatel audio chipset.  The laptop only has one headphone jack and a mic jack.  In Windows, I found (by accident) that I could switch the mic jack to a line out with the driver, but I never had a reason to.  Now, I am looking to purchase some 5.1 speakers (which need an extra line out), and i would like to use this switch, but currently I only run XP in virulatization.  I did some googling and found what appears to  be source code for a patch that is included in the 2.6.17 kernel (which I am running with edgy) but I do not know how to use it, here is the snippet of code from [http://www.gelato.unsw.edu.au/lxr/source/sound/pci/hda/patch_sigmatel.c](http://www.gelato.unsw.edu.au/lxr/source/sound/pci/hda/patch_sigmatel.c) that show the switch.

768         if (spec->line_switch)
769                 if ((err = stac92xx_add_control(spec, STAC_CTL_WIDGET_IO_SWITCH, "Line In as Output Switch", cfg->input_pins[AUTO_PIN_LINE] << 8)) < 0)
770                         return err;
771 
772         if (spec->mic_switch)
773                 if ((err = stac92xx_add_control(spec, STAC_CTL_WIDGET_IO_SWITCH, "Mic as Output Switch", (cfg->input_pins[AUTO_PIN_MIC] << 8) | 1)) < 0)
774                         return err;
775 
776         return 0;
777 }

Does anyone know how to use this to make my mic port a line out?

---

