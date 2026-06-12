---
title: "sound card"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by rtrujillo on 2005-07-05
Hello,

I'm new on ubuntu. I've just installed ubuntu 5.04 on muy notebook, but i have a problem with my sound card.

lspci tells me it's an intel, but when i tried to use alsaconf to configure alsa, bash tells me that this command doesn't exists. I have alsa-base and asla-utils installed, and even i reinstalled both.

If i tried to run alsamixer, i get an error ( i supose it's becouse there isn't any driver loaded ). It's the default instalation of ubuntu, anywone can help me?

Thanks,

R. trujillo

---

### Post by andlinux21 on 2005-07-05
Please check the HOWTO's first and if that doesnt work do a search of the forums.
I had problems with my Micron Transport laptop not seeing the sound card at all but I ended up adding line to the startup module and now I have sound so maybe that will work for you also.

---

### Post by rtrujillo on 2005-07-05
No sorry, this doesn't works.

I checked howtos, but all i have is howto configure sound under ubuntu using alsaconf. I don't have this command, and my question is if this comes with ubuntu or not. 

The only way to configure alsa is downloading alsa-src and biulding it? not using the synaptic or default instalacion tools?

thanks.

---

### Post by Trace Green on 2005-07-10
OK, Ubuntu did the same thing like alsaconf when config your sound card, please tell me lspci and lspci -n and lsmod first. :-D

---

