---
title: "SB Audigy eX Ir port"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by WattoDaToydarian on 2005-02-18
Hey guys, i'v been trying to get the Ir port on the external drive for my SB Audigy eX to work so i can use it with lirc. I put the "options snd-emu10k1 enable_ir=1" in the /etc/modules.conf file at the very end and I used the "cat /dev/snd/midiC0D0" and "cat /dev/snd/midiC0D1" commands while pressing remote buttons and nothing showed up. ](*,)  Please tell me what the problem is people!
Thanks.

---

### Post by WattoDaToydarian on 2005-02-25
Come on guys, I really need help here! I would appreciate any thoughts you can provide.

Thanks.

---

### Post by zenyatta on 2005-10-29
The options have to be added into /etc/modprobe.d/alsa-base - it takes precedence over both /etc/modules.conf and /etc/modutils/alsa-base. I just spent half a day figuring it out.

Anyway: there is a line in /etc/modprobe.d/alsa-base which goes

install snd-emu10k1 modprobe --ignore-install snd-emu10k1 && { /lib/alsa/modprobe-post-install snd-emu10k1 ; modprobe --quiet snd-emu10k1-synth ; }

and you want to change it to

install snd-emu10k1 modprobe --ignore-install snd-emu10k1 **extin=0x3fcf extout=0x1fcf enable_ir=1** && { /lib/alsa/modprobe-post-install snd-emu10k1 ; modprobe --quiet snd-emu10k1-synth ; }

Of course, exact values of extin and extout depend on the model of SBLive that you're using - I suppose you could even leave them out and only insert "enable_ir=1".

Hope this helps.

z.

---

