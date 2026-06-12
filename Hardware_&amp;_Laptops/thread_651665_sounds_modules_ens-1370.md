---
title: "sounds modules ens-1370"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by Smbrandes on 2007-12-27
Hello,

   After acquiring another convert to Ubuntu, I had the surprise of finding that getting the sound to work under Gibbon, has become an intractable problem. I followed the whole routine set forth in the sound problems page. I put in a fresh kernel compiled the drivers etc. It appeared happy enough, but when using aplay -l in terminal it it still gives a no sound device error. Beats me as to why. Since the modprobe command does not result in any errors. The alsa installation compiling gave no errors, just the warning the default state for the channel is muted. which would be nice if it was muted and simply not loaded. So it is a dual boot box and the sound card works dandy on the windows side. For whatever reason it refuse to accept a sound module. Also there appears to be some notational confusion about what actually the sound card is. The lpci-l yields es1370 rev1, yet the alsa documentation states it is termed ens1370. Absolutely mystified as the sound card worked previously under Fawn and broke when installing Gibbon. Not upgrading, installing from a live cd. Should I go back to fawn or retry a total reinstall? Or is there some bizarre bug that can be overcome?

---

### Post by Smbrandes on 2008-01-26
After a total reinstall, nothing however all other parameters remain unchanged,  However on using dmesg there is an error concerning the loading of the ENS1370 it is thus "   49.236833] ENS1370: probe of 0000:00:0c.0 failed with error -16". where does one find a list of error codes for the dmesg? what does this represent, an irq conflict? Or something else?

---

### Post by Smbrandes on 2008-02-03
After trying another card:

00:0c.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI128
        Flags: slow devsel, IRQ 10
        I/O ports at d600 [size=64]
        Capabilities: <access denied>

 Nothing happens once again. Here though we find a weird thing happening I tried putting the card in a different pci slot after removing the other and then the ethernet card ceases to work if I put it the slot the other sound was in the ethernet card works but not the soundcard. what on earth is causing this nonsense?

---

