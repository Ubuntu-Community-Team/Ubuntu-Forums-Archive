---
title: "toshiba a60 sound problem"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by ioubuntu on 2005-04-28
well i'll be really thankfull if someone could give me some help 
i got a toshiba a60 intel P4 2.8 ghz, when i installed the hoary preview i386 bin-1 i got  sound work really well....upgrading distro to the release or installing a fresh copy of the release i'm not able to get sound working....after a lot of try reading something around here and other forums i was able (putting pci=noacpi on kernel option) to hear something on login screen...but that sound never stop...and with that option i'm not able to use internet (i use it trought lan).

PLLLLZZZZ help me .....i'm driving crazy
ty very much to all

PS sorry my little english ;)

---

### Post by lucus on 2005-05-01
all i can tell people is how my sound started to work

modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530

try something similar for your sound card

modprobe snd-            dma 1=   dma 2=     fm_port=   irq=   isapnp=   midi_port=   port =  sb_port=  wss_port=


just insert your sound card's values into those fields.... good luck

---

