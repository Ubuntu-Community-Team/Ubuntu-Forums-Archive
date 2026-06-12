---
title: "Some hardware not working..."
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by joshlink01 on 2005-06-20
Hi. I have just switched to Ubuntu and I have never used Linux before so...

I am having problems with my sound (looks like im not the only one) and it is a Creative Audigy2 Z5 Platinum Pro 

I can't get my TV tuner to work:
Studio TV Terminator 

And I can't find drivers for my printer:
HP PSC 750


All help is welcome! :)

---

### Post by hw-tph on 2005-06-20
[QUOTE=joshlink01]Hi. I have just switched to Ubuntu and I have never used Linux before so...

I am having problems with my sound (looks like im not the only one) and it is a Creative Audigy2 Z5 Platinum Pro 

I can't get my TV tuner to work:
Studio TV Terminator 

And I can't find drivers for my printer:
HP PSC 750


All help is welcome! :)[/QUOTE]
 It seems your tuner card isn't supported - [yet](http://lists.zerezo.com/video4linux/msg00356.html). 

The printer is supposed to work with the standard [hpijs driver](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_750).

The snd-emu10k1 Alsa driver should be able to drive that card if I'm not correct (the Alsa website with the [soundcard matrix](http://www.alsa-project.org/alsa-doc) is down at the moment) and shouldn't pose much of a problem. Type **lspci** to verify it really is emu10k?-based.


Håkan

---

