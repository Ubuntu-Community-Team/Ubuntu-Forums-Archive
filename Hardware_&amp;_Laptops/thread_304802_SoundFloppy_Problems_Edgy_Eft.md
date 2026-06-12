---
title: "Sound/Floppy Problems Edgy Eft"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by LDRoamer on 2006-11-22
I am using edgy on my old laptop and I have a bit of an issue with the sound.  My machine uses an ESS1869 chip. The sound chip is not detected automatically and I have to force the loading of the driver. If I try to manually load the correct driver (snd_es18xx) without any options it returns an error. Loading the driver and explicitly specifying all the options will allow it load. However in order to get the sound to work I had to change one of the options from its correct setting. I had to set the option dma2=5 to dma2=2 to get sound (and the sound works perfectly using that). Lspnp however tells me 5 is the correct setting.  I believe that by changing the sound settings I may have disabled my floppy drive. When I try to use the floppy I get a message that it can't mount it because its not a block device. 

Its possible the two are not related but my reason for guessing that they are is that I am also trying out Debian Etch. Using the dma2=2 option in Etch I notice an error on boot up that says "cannot grab dma2 for floppy". Unlike Ubuntu though in Etch I have no sound regardless of which dma option I select.

I could live without the floppy and except for this issue Ubuntu has been pretty good on this old hardware.

---

### Post by LDRoamer on 2006-11-29
Just an update. I have my floppy working now by changing the parameter dma2=2 to dma2=0 in the sound configuration.  I haven't actually changed the settings in the bios for the sound chip (Bios says dma is 5). I didn't want to mess with the BIOS for fear that I would mess up my WinXP setup (I am dual booting). I selected dma2=0 because the bios offers an alternate configuration that uses dma 1 and 0 instead of dma 1 and 5. I guessed that dma 0 might be available. I have no idea, though, why this should work when the bios is set to dma 5 for the sound chip.

Using what should be the correct configuration (dma2=5) resulted in no sound and gnome loaded very slowly. Interestingly enough if I use dma2=5 and I type in my password wrong at the logon screen I do get the drum roll telling you that there is an error. However once you log in everything goes in the crapper.

I don't know if I have broken something else now but so far so good. I will keep my fingers crossed.

---

