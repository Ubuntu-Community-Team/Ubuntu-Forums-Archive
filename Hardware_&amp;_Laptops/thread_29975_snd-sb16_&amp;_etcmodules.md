---
title: "snd-sb16 &amp; /etc/modules"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by Bloke on 2005-04-26
Hello. Ubuntu search to configure a Creative Labs Sound Blaster 16 results in : 

[http://www.ubuntuforums.org/showthread.php?t=375&highlight=sb16](http://www.ubuntuforums.org/showthread.php?t=375&highlight=sb16)
[http://www.ubuntuforums.org/showthread.php?t=1805&highlight=sound+blaster+16+ISA](http://www.ubuntuforums.org/showthread.php?t=1805&highlight=sound+blaster+16+ISA)

And: 

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Vibra16X.&chip=sb16&module=sb16)

My question is this = Fedora detects the card and adds the following to modprobe.conf (modprobe.conf is to Fedora, as modules is to Ubuntu) ... :

--------------------------------------------------------------------------
alias snd-card-0 snd-sb16
options snd-card-0 index=0
install snd-sb16 /sbin/modprobe --ignore-install
snd-sb16 && /usr/sbin/alsactl restore >/dev/null 2>&1 || : remove snd-sb16 { /usr/sbin/alsactl store >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-sb16
--------------------------------------------------------------------------

... will the above work for Ubuntu??

---

