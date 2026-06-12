---
title: "Toshiba A60, Sound problem"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by alquimista on 2005-07-21
Hi,
I checked a previous post  where for this Notebook (A60, Satellite) there was a suggestion for sound problem:
------------------------------------------
You have to follow the instructions on this page : [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

And after add these lines to these files :

/etc/hotplug/blacklist :
snd-atiixp-modem
snd-atiixp

/etc/modules :
snd-atiixp

You also have to type "chmod 777 /dev/dsp"

------------------------------------------
I followed these steps, yet I get the same error:
Sound server informational message:
Error while initializing the sound driver:
device: default can't be opened for playback (No such device)
The sound server will continue, using the null output device.

I'd appreciate any help.

Thanx,
Guillermo

---

