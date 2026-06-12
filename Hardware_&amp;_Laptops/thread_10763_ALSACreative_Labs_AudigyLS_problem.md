---
title: "ALSA/Creative Labs AudigyLS problem"
date: 2005-01-11
forum: Hardware &amp; Laptops
---

### Post by malegria on 2005-01-11
Ok. I followed the instructions as per the following website for ALSA:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=audigyls#modp](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=audigyls#modp)
 
As you can see I'm running a Creative Labs Audigyls card. And when I try to do:
 modprobe snd-audigyls;modprobe snd-pcm-oss;modprobe snd-mixer-oss;modprobe snd-seq-oss

I get this:
FATAL: Module snd_audigyls not found.

Does this make any sense? I even recompiled the kernel making sure my card was supported.

Any ideas? (BTW, I've been able to make this card run under FC3)

Thanks.

---

### Post by malegria on 2005-01-16
I have found the solution. 

I gave up on Ubuntu, and then came back. This time I made sure to install both the kernel(linux, in Ubuntu) sources AND the headers. And then I tried to re-install ALSA(beware the name for audigyls in 1.0.8 is "ca0106" not "audigyls"), and then IT WORKS!!!

---

