---
title: "Compaq Deskpro - missing info"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by Oceola on 2006-05-18
I have a Compaq Deskpro EP with a 550 Mhz Katmai PIII processor.
When I upgraded to Breezy all the detailed information like dip switch positions and address info, including the Katmai ID are missing from the "Device Manager"

Any thoughts other than I should get a new computer?
I have the manual so the loss of dip info isn't a big deal but there was whole lot more info. It does recognize the 440BX chip set but doesn't pick up on the Katmai.

One other small problem is a missing "dri" file for the Matrox MGA G200 AGP display card/chipset. I picked up the latest driver and src files from Matrox, can I just place the file once I find it, in the directory which the Xorg log files tells me it can't find it.
It's not there. This worked for Sound to make audacity export Mp3's.
Missing file is "libdri.a"

Thanks:-k

---

### Post by az on 2006-05-18
[QUOTE=Oceola]I have a Compaq Deskpro EP with a 550 Mhz Katmai PIII processor.
When I upgraded to Breezy all the detailed information like dip switch positions and address info, including the Katmai ID are missing from the "Device Manager"[/QUOTE]

I think the device manager is just less verbose than before.  All that info should still be there.  Run "lshw -v -v".  Also, look in /proc.

[QUOTE=Oceola]
Any thoughts other than I should get a new computer?.[/QUOTE]

Why?  I have one of those too.  I like it.

[QUOTE=Oceola]
I have the manual so the loss of dip info isn't a big deal but there was whole lot more info. It does recognize the 440BX chip set but doesn't pick up on the Katmai.[/QUOTE]

So what?  What is the problem?  
[QUOTE=Oceola]

One other small problem is a missing "dri" file for the Matrox MGA G200 AGP display card/chipset. I picked up the latest driver and src files from Matrox, can I just place the file once I find it, in the directory which the Xorg log files tells me it can't find it.
It's not there. This worked for Sound to make audacity export Mp3's.
Missing file is "libdri.a"

Thanks:-k[/QUOTE]
DRI should be enabled by default.  How much memory does your card have and what is the default screen resolution?  Ubuntu tries to use the maximum resolution and that can sometimes chew up all the memory you would need to run 3d acceleration.

You can reconfigure the xserver to use less memory by setting the maximum resolution and color depth lower.  Even if you don't use those resolutions, the maximum resolution and color depth memory is set aside.

---

### Post by Oceola on 2006-05-18
Thanks for the speedy response, azz.
I'll try this and Yes, it is a good box and I like it as well.
I just thought something may have been overlooked or left out.

The problem was there was a lot more address information and a lot more detail and I was concerned I might be having a fault in the Kernal identifying bits and pieces. The device manager shows everything else on the machine splendidily.

On the DRI issue, I went back and checked, the card has 16 MB memory and the DRI requirement is 15.36 MB You were right about available memory, I misread and thought it was a missing file. I'm running reduced as it is at 1024x768 and I have the font display dialed down. 

Is it possible to remove some of the display drivers which are loaded for other machines like the nvidia stuff and some of the xorg drivers without losing the Ubuntu Desktop. Everytime I want to remove the drivers it tells me the desktop will go with it, so I have not removed them.

---

### Post by az on 2006-05-22
[QUOTE=Oceola]
Is it possible to remove some of the display drivers which are loaded for other machines like the nvidia stuff and some of the xorg drivers without losing the Ubuntu Desktop. Everytime I want to remove the drivers it tells me the desktop will go with it, so I have not removed them.[/QUOTE]

Xorg will be better modularised in future releases.  Currently, you either live with all the extra drivers, or live without the ubuntu desktop metapackage.

---

