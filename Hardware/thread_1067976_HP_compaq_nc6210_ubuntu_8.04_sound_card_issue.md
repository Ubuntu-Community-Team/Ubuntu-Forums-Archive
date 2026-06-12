---
title: "HP compaq nc6210 ubuntu 8.04 sound card issue"
date: 2009-02-12
forum: Hardware
---

### Post by visciousirene on 2009-02-12
Dear all,

I have recently moved to the Ubuntu OS as I was fed up of windows and its ways....

So far I am quite happy but it is rather complicated to get this sound card issue straight.

I have tried a load of different things and nothing worked so far, I am also a super beginner so I don't have a clue about things like the terminal and shell, but I did try!

Anyhow, the major problems are when I play a song with VLC after it ahs ended there's a noise like a guitar amplifier when not playing that remains on....

Secondly the mic-in slot (jack type) isn't working, I have tried everything I have found to solve this but there's no signal going in, either with a sound recorder nor the lingot guitar tuner nor the creox c program for guitars.

Does anybody know what I should do?

I have tried a few of the fixes I have found in the forums and on-line but none of it worked, I know from the alsa website that I don not have the right driver for my sound card which is ICH southbridge AC97 audio, when I follow the instructions on the page [http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0), it says that I cannot do mkdir alsa....

The driver that comes up when inserting the command modinfo soundcore is 
filename:     /lib/modules/2.6.24-23-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.24-23-generic SMP mod_unload 586 

Thanks to anyone who will help me with this!!!!

irene

---

