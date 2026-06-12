---
title: "Overclocking nVidia card"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by Gags666 on 2005-05-24
Hi,

I've got a GeForce 6800 GT which runs perfect as Ultra under Windows XP. Now I'd like to overclock my card under Linux as well but nvclock won't run - it only brings me up a "segmentation fault" on every command even after reinstalling it. But I also heard nvclock should not be very reliable so I think I didn't want to use it even if it would work. Isn't there any other way to overclock my card like some option added to the xorg.conf or something like that? I don't want to be forced to make modifications to the BIOS of my card as long it's not the last alternative.

---

### Post by Arktis on 2005-07-10
Same problem here.  I'm going to try installing from the source tar.gz...

Installation form source went okay, but running the gtk version of nvclock still gives a segfault.  Running the command line version seems to work fine as far as I can tell, but output of nvclock -i claims my card is too new to be supported and that to continue would be dangerous.  So, I uninstalled it.

---

### Post by mosibfu on 2008-04-19
just add Option "Coolbits" "1" to the device section of ur 3d card in xorg.conf and then nvidia-xserver settings or nvidia-settings whatever, will have an overclocking setting.. it just doesnt save at boot..

(my device section)
```
Section "Device"
    Identifier     "Geforce8500GT_1"
    Driver         "nvidia"
    Busid          "PCI:1:0:0"
    Option         "Coolbits"      "1"
    VendorName     "NVIDIA Corporation"
EndSection
```

quick fix:

make a script that runs at start, like this(my overclock3d.sh):
```
nvidia-settings --assign "GPUOverclockingState=1"
nvidia-settings --assign "GPU3DClockFreqs=700,510"
nvidia-settings --assign "GPU2DClockFreqs=700,510"
```

u will need to update the command's with your clock speeds (700 is my gpu, 510 is my memory) and if you use nvidia xserver settings thing, you need to replace nvidia-settings by its command. (same program different command) (or just install nvidia-settings for this script)

erm whats next, ohh yeah, the new driver supports powermizer, wich will clock back, disable its update at the bottom tab of nvidia settings, (nvidia-settings Configuration) and it wont bother you again ur clocks stays at overclock..

so just to make it clear, no use for nvclock anymore, its all in the driver

---

### Post by Merdril on 2008-05-10
I have a mobile gpu (GeForce Go 6150 on nForce 430) and will overclocking work on a mobile gpu?

---

### Post by Posterus on 2008-05-11
> **Merdril said:**
> I have a mobile gpu (GeForce Go 6150 on nForce 430) and will overclocking work on a mobile gpu?

I dont think so, i have a mobile gpu also (6600) and i enabled coolbits and if you go the the nvidia-settings, the auto-detect button in the overclock menu is grayed out and if you manually change the frequencies and click apply they revert right back to default settings, i read the help file and it says that the OC feature is only for FX series and newer non-mobile units =\  anybody know a work around for this?(if any at all) cuz i can get ALOT more out of my card if i do this, i can do this under windows just fine.

---

