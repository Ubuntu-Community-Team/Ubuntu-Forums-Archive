---
title: "No line-out in alsa mixer"
date: 2009-08-29
forum: Hardware
---

### Post by WabbitTwax on 2009-08-29
Hi, there. I' m using Ubuntu 8.04 on a laptop with a VIA sound card. The problem is that headphones won't work. When I plug them in, the pc speaker goes silent like it is supposed to, but no sound comes out of the headphones. And there is no 'headphones' or 'line-out' control in alsa mixer. Yes, and everything works fine on Windows, so my headphones are not broken. Any sudgestions?

---

### Post by jerrrys on 2009-08-29
Volume Control>Edit>preferences; should allow you to add headphones

---

### Post by WabbitTwax on 2009-08-31
Yeah, i know, but there are no headphones in the preferences.

---

### Post by jerrrys on 2009-08-31
???

[attach]126934[/attach]

---

### Post by WabbitTwax on 2009-08-31
I fixed my problem after experimenting with switching everything on and off in alsamixer. 

I had to turn on 'surround', 'duplicate front' and crank 'VIA DXS' up to max. 
now my headphones work. It's hydrogen time!

---

