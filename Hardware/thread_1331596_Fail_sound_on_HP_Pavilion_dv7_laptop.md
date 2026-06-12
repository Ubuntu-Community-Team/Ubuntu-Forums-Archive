---
title: "Fail sound on HP Pavilion dv7 laptop"
date: 2009-11-19
forum: Hardware
---

### Post by Exüberance on 2009-11-19
I have a HP Pavilion dv7 laptop that came with Vista, but I have installed Ubuntu on it. The laptop has a subwoofer on the bottom and, aside from the days when Vista decides it doesn't want to load random drivers, it works perfectly fine on Vista. It sounds as it should. It uses IDT High Definition Audio Codec as the sound driver.

On Ubuntu, however, the sound quality is relatively bad since it doesn't use the subwoofer at all.

Adding model=hp to the end of my alpha-base.conf file did absolutely nothing. Adding model=ref added 2 entires to the list of sound profiles, but it made all profiles (including the one which worked before) not work at all, on any speaker (even headphones).

Is there any way to fix this or any drivers I can download that support a built-in subwoofer?

---

### Post by Exüberance on 2009-11-22
b-b-b-b-bump

---

### Post by Exüberance on 2009-11-27
I have tried changing the alsa-base.conf file, but one of the time I did sudo also force-reload, the sound card dissapeared from the sound preferences, and even after I reverted back to my old alsa-base.conf file, it still won't show up so now I don't even have ANY sound from ANY speakers or headphones. <_<

---

### Post by PreThunder on 2010-02-04
Bump

Same problem as you describe with my Acer Aspire 7738G

---

