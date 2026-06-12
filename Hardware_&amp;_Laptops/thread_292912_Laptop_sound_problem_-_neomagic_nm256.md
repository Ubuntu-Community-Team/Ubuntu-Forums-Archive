---
title: "Laptop sound problem - neomagic nm256"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by qopax on 2006-11-04
This problem has been haunting me for a few months now. Several times I've tried finding solutions by google and ubuntu forums, but most of them were inconsistent, inconclusive, and usually caused more problems than they solved. I've just installed edgy ubuntu-server, so I thought I might try finding a fix for the last time, before I just give up on getting the sound card to work.

This is the message I get while booting:

[   49.527562] PCI: Found IRQ 11 for device 0000:00:02.1
[   49.527640] nm256: no ac97 is found!
[   49.527710]   force the driver to load by passing in the module parameter
[   49.527775]     force_ac97=1
[   49.527827]   or try sb16 or cs423x drivers instead.


what lspci shows:

00:02.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 12)


The laptop is a Compaq Solo 3150.


Any suggestions? I'm still mostly a linux newb, so clear instructions are welcome, but I don't mind googling the correct usage of any commands.

---

### Post by ingo on 2006-11-05
a quick google came up with this:

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Neomagic&card=MagicMedia+256AV.&chip=NM2200&module=nm256](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Neomagic&card=MagicMedia+256AV.&chip=NM2200&module=nm256)

that should see (hear) you right :)

---

### Post by Pianoman72 on 2006-11-06
Please search for a thread under my username and keyword neomagic - post your results in that thread, please.

EDIT - here is the link <http://www.ubuntuforums.org/showthread.php?t=284405>

I noticed you do not have an Inspiron but you are having the same problem I had...so just let me know if my instructions are any good and maybe we can change that thread so it references your machine as well.

---

