---
title: "Thinkpad 770x no sound"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by gishnob on 2006-06-09
Im running xubuntu on a thinkpad 770x, so far im loving it alot, however, i cannot get my sound to work. Can anyone please help me out?

---

### Post by siriusnova on 2006-06-10
did you check the thinkpad linux wiki? this is a known problem

[http://thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads](http://thinkwiki.org/wiki/Problem_with_broken_sound_on_some_ThinkPads)

---

### Post by gishnob on 2006-06-10
I tried it, still not working when i try to type:

modprobe cs4232 io=0x530 irq=5 dma=1 dma2=0 mpuio=0x330 mpuirq=7 synthio=0x330 synthirq=7

in terminal, i get:

vic@Laptop:/lib/modules/2.6.15-23-386/kernel/sound/isa/cs423x$ sudo modprobe cs4232 io=0x530 irq=5 dma=1 dma2=0 mpuio=0x330 mpuirq=7 synthio=0x330 synthirq=7
FATAL: Module cs4232 not found.

I really want to use linux on my thinkpad, xubuntu runs so damn good on this thing. I just need sound!

---

### Post by siriusnova on 2006-06-11
try snd-cs4232 instead of just cs4232

---

### Post by gishnob on 2006-08-06
sudo modprobe snd-cs4232 io=0x530 irq=5 dma=1 dma2=0 mpuio=0x330 mpuirq=7 synthio=0x330 synthirq=7
Password:
FATAL: Error inserting snd_cs4232 (/lib/modules/2.6.15-23-386/kernel/sound/isa/cs423x/snd-cs4232.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by rafusmx on 2006-08-13
[FONT="Verdana"]Hi!

I'm having the same problem here with my TP600. I had some trouble with debian but it worked all right after modprobing cs4232. 

I wanted to test Ubuntu, but I can't make the sound work... I tried to search the module manualy, but it seems like "snd-cs4232" module isn't on the kernel folder that the error message shows...

FATAL: Error inserting snd_cs4232 snd_cs4232 (/lib/modules/2.6.15-26-386/kernel/sound/isa/cs423x/snd-cs4232.ko): No such device

I searched and the sound directory doesn't even exists on this modules foldier...

I'll be installing it on my desktop PC, to try to find out something... If you find anything usefull it will be great.[/FONT]

---

### Post by szabigalambosi on 2006-08-17
Please check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=230076](http://www.ubuntuforums.org/showthread.php?t=230076)

Cheers, Szabi

---

