---
title: "VIA 8235 sound coming out of wrong jack"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by lerouxb on 2005-07-19
I have ubuntu and windows running dual boot. In windows I plug my speakers into the green plug (the correct one) and in linux I have to plug it into the pink one (for microphones).

I spend most of my time in linux, but it is annoying to have to climb under the table every time I want  to play games  ;-) 

this is the relevant line from lspci:
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

(it is a via kt400 chipset motherboard with onboard audio)

Is there any way to swap the meaning of the different plugs (don't know the correct terminology) around? Obviously there must be, because linux chose the wrong one and sound works perfectly...

Le Roux

---

### Post by lerouxb on 2005-07-19
wait a minute... I lied. windows is the wrong way around..

Will try and click around in XP.

---

### Post by lerouxb on 2005-07-19
ok. I was still wrong. In windows it is in the pink plug, in linux in die blue plug.

So both of them are wrong.

I can't change it in windows, so I am hoping linux has a way of changing it so that I can at least get it to use the same wrong plug windows does.

I'm very close to just buying a cheap soundcard ;)

(yes. I have fiddled with everything in alsamixer...)

---

