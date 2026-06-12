---
title: "problem with soudcard on compaq armada 1573D"
date: 2008-04-29
forum: Hardware
---

### Post by mvst on 2008-04-29
Hi all!

I have a little problem with my old 233 mhz compaq laptop.
Everything exept for the soudcard is working.

I know it is an alsa snd-es18xx compatible card but i cant seem to get it to work, mp3blasters keeps telling me there is no sound device. Oh and bedore i forget i think its an ISA card.

As i have found out using hirens boot cd it is an ess 1878 adiodrive soundcard
with the following settings:
220H
irq5
dma1
sb16 high dma 0

Can anyone help me with this?

---

### Post by mvst on 2008-04-29
problem solved

compaq armada 1573D standard settings for sound

modprobe snd-es18xx port=0x220 irq=5 dma1=1 dma2=0 isapnp=0

this worked for me! all thanks to hirens for getting me the adresses

---

